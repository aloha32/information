相关链接：
- [https://modelcontextprotocol.io/introduction](https://modelcontextprotocol.io/introduction)
- [MCP 起源于 **2024 年 11 月 25 日** Anthropic 发布的文章](https://www.anthropic.com/news/model-context-protocol)
- [MCP (Model Context Protocol)，一篇就够了。](https://zhuanlan.zhihu.com/p/29001189476)

# 什么是MCP？
MCP （Model Context Protocol，模型上下文协议）定义了应用程序和 AI 模型之间交换上下文信息的方式。
这使得开发者能够以一致的方式将各种数据源、工具和功能连接到 AI 模型（一个中间协议层）。
MCP 的目标是创建一个通用标准，使 AI 应用程序的开发和集成变得更加简单和统一。
![image](https://github.com/user-attachments/assets/623f200e-09ed-49be-acf3-43fd9a9c395b)
![image](https://github.com/user-attachments/assets/9e20501c-6cc6-417e-86e9-47a85a644057)

# 为什么需要MCP？
MCP 的出现是 prompt engineering 发展的产物。更结构化的上下文信息对模型的 performance 提升是显著的。

想象一下没有 MCP 之前我们会怎么做？我们可能会人工从数据库中筛选或者使用工具检索可能需要的信息，手动的粘贴到 prompt 中。随着我们要解决的问题越来越复杂，手工把信息引入到 prompt 中会变得越来越困难。

为了克服手工 prompt 的局限性，许多 LLM 平台（如 OpenAI、Google）引入了` function call `功能。这一机制允许模型在需要时调用预定义的函数来获取数据或执行操作，显著提升了自动化水平。

` function call `平台依赖性强，不同 LLM 平台的 function call API 实现差异较大。例如，OpenAI 的函数调用方式与 Google 的不兼容，开发者在切换模型时需要重写代码，增加了适配成本。除此之外，还有安全性，交互性等问题。

数据与工具本身是客观存在的，只不过我们希望将数据连接到模型的这个环节可以更智能更统一。Anthropic 基于这样的痛点设计了 MCP，充当 AI 模型的"万能转接头"，让 LLM 能轻松的获取数据或者调用工具。更具体的说 MCP 的优势在于：

- 生态 - MCP 提供很多现成的插件，你的 AI 可以直接使用。
- 统一性 - 不限制于特定的 AI 模型，任何支持 MCP 的模型都可以灵活切换。
- 数据安全 - 你的敏感数据留在自己的电脑上，不必全部上传。（因为我们可以自行设计接口确定传输哪些数据）

# 作为用户，如何使用MCP？
具体的使用方式参考官方文档：[For Claude Desktop Users](https://modelcontextprotocol.io/quickstart/user)。这里不再赘述，配置成功后可以在 Claude 中测试：Can you write a poem and save it to my desktop? Claude 会请求你的权限后在本地新建一个文件。

官方也提供了非常多现成的 MCP Servers:
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers)
- [MCP Servers Website](https://mcpservers.org/)
- [Official MCP Servers](https://github.com/modelcontextprotocol/servers)

# MCP Architecture 解构
官方的架构图:
![image](https://github.com/user-attachments/assets/02824fc1-ca5a-4bc5-b0b9-930518ddc6e4)

MCP 由三个核心组件构成：Host、Client 和 Server。实际场景来理解:

假设你正在使用 Claude Desktop (Host) 询问："我桌面上有哪些文档？"

Host：Claude Desktop 作为 Host，负责接收你的提问并与 Claude 模型交互。
Client：当 Claude 模型决定需要访问你的文件系统时，Host 中内置的 MCP Client 会被激活。这个 Client 负责与适当的 MCP Server 建立连接。
Server：在这个例子中，文件系统 MCP Server 会被调用。它负责执行实际的文件扫描操作，访问你的桌面目录，并返回找到的文档列表。
整个流程是这样的：你的问题 → Claude Desktop(Host) → Claude 模型 → 需要文件信息 → MCP Client 连接 → 文件系统 MCP Server → 执行操作 → 返回结果 → Claude 生成回答 → 显示在 Claude Desktop 上。

这种架构设计使得 Claude 可以在不同场景下灵活调用各种工具和数据源，而开发者只需专注于开发对应的 MCP Server，无需关心 Host 和 Client 的实现细节。

![image](https://github.com/user-attachments/assets/8f61c400-bff3-4717-9b64-4d0d615b2c0d)

# 原理：模型是如何确定工具的选用的？
Claude（模型）是在什么时候确定使用哪些工具的呢？

当用户提出一个问题时：

1. 客户端（Claude Desktop / Cursor）将你的问题发送给 Claude。
2. Claude 分析可用的工具，并决定使用哪一个（或多个）。
3. 客户端通过 MCP Server 执行所选的工具。
4. 工具的执行结果被送回给 Claude。
5. Claude 结合执行结果构造最终的 prompt 并生成自然语言的回应。
6. 回应最终展示给用户！

深入源码。显然这个调用过程可以分为两个步骤：

1. 由 LLM（Claude）确定使用哪些 MCP Server。
2. 执行对应的 MCP Server 并对执行结果进行重新处理。

![image](https://github.com/user-attachments/assets/eda5f328-3401-46a8-9896-644d8a6e8438)

## 模型如何智能选择工具？
先理解第一步模型如何确定该使用哪些工具？通过阅读代码，可以发现模型是**通过 prompt **来确定当前有哪些工具。我们通过将工具的具体使用描述以文本的形式传递给模型，供模型了解有哪些工具以及结合实时情况进行选择。

```python
... # 省略了无关的代码
 async def start(self):
     # 初始化所有的 mcp server
     for server in self.servers:
         await server.initialize()
 ​
     # 获取所有的 tools 命名为 all_tools
     all_tools = []
     for server in self.servers:
         tools = await server.list_tools()
         all_tools.extend(tools)
 ​
     # 将所有的 tools 的功能描述格式化成字符串供 LLM 使用
     # tool.format_for_llm() 我放到了这段代码最后，方便阅读。
     tools_description = "\n".join(
         [tool.format_for_llm() for tool in all_tools]
     )
 ​
     # 这里就不简化了，以供参考，实际上就是基于 prompt 和当前所有工具的信息
     # 询问 LLM（Claude） 应该使用哪些工具。
     system_message = (
         "You are a helpful assistant with access to these tools:\n\n"
         f"{tools_description}\n"
         "Choose the appropriate tool based on the user's question. "
         "If no tool is needed, reply directly.\n\n"
         "IMPORTANT: When you need to use a tool, you must ONLY respond with "
         "the exact JSON object format below, nothing else:\n"
         "{\n"
         '    "tool": "tool-name",\n'
         '    "arguments": {\n'
         '        "argument-name": "value"\n'
         "    }\n"
         "}\n\n"
         "After receiving a tool's response:\n"
         "1. Transform the raw data into a natural, conversational response\n"
         "2. Keep responses concise but informative\n"
         "3. Focus on the most relevant information\n"
         "4. Use appropriate context from the user's question\n"
         "5. Avoid simply repeating the raw data\n\n"
         "Please use only the tools that are explicitly defined above."
     )
     messages = [{"role": "system", "content": system_message}]
 ​
     while True:
         # Final... 假设这里已经处理了用户消息输入.
         messages.append({"role": "user", "content": user_input})
 ​
         # 将 system_message 和用户消息输入一起发送给 LLM
         llm_response = self.llm_client.get_response(messages)
 ​
     ... # 后面和确定使用哪些工具无关
     
 ​
 class Tool:
     """Represents a tool with its properties and formatting."""
 ​
     def __init__(
         self, name: str, description: str, input_schema: dict[str, Any]
     ) -> None:
         self.name: str = name
         self.description: str = description
         self.input_schema: dict[str, Any] = input_schema
 ​
     # 把工具的名字 / 工具的用途（description）和工具所需要的参数（args_desc）转化为文本
     def format_for_llm(self) -> str:
         """Format tool information for LLM.
 ​
         Returns:
             A formatted string describing the tool.
         """
         args_desc = []
         if "properties" in self.input_schema:
             for param_name, param_info in self.input_schema["properties"].items():
                 arg_desc = (
                     f"- {param_name}: {param_info.get('description', 'No description')}"
                 )
                 if param_name in self.input_schema.get("required", []):
                     arg_desc += " (required)"
                 args_desc.append(arg_desc)
 ​
         return f"""
 Tool: {self.name}
 Description: {self.description}
 Arguments:
 {chr(10).join(args_desc)}
 """
```

那 tool 的描述和代码中的 input_schema 是从哪里来的呢？

通过进一步分析 MCP 的 Python SDK 源代码可以发现：大部分情况下，当使用装饰器 @mcp.tool() 来装饰函数时，对应的 name 和 description 等其实直接源自用户定义函数的函数名以及函数的 docstring 等。

```python
 @classmethod
 def from_function(
     cls,
     fn: Callable,
     name: str | None = None,
     description: str | None = None,
     context_kwarg: str | None = None,
 ) -> "Tool":
     """Create a Tool from a function."""
     func_name = name or fn.__name__ # 获取函数名
 ​
     if func_name == "<lambda>":
         raise ValueError("You must provide a name for lambda functions")
 ​
     func_doc = description or fn.__doc__ or "" # 获取函数 docstring
     is_async = inspect.iscoroutinefunction(fn)
     
     ... # 更多请参考原始代码...
```

总结：**模型是通过 prompt engineering，即提供所有工具的结构化描述和 few-shot 的 example 来确定该使用哪些工具。**另一方面，Anthropic 肯定对 Claude 做了专门的训练（毕竟是自家协议，Claude 更能理解工具的 prompt 以及输出结构化的 tool call json 代码）

## 工具执行与结果反馈机制
把 system prompt（指令与工具调用描述）和用户消息一起发送给模型，然后接收模型的回复。当模型分析用户请求后，它会决定是否需要调用工具：

- 无需工具时：模型直接生成自然语言回复。
- 需要工具时：模型输出结构化 JSON 格式的工具调用请求。

如果回复中包含结构化 JSON 格式的工具调用请求，则客户端会根据这个 json 代码执行对应的工具。

如果模型执行了 tool call，则工具执行的结果 result 会和 system prompt 和用户消息一起重新发送给模型，请求模型生成最终回复。

如果 tool call 的 json 代码存在问题或者模型产生了幻觉怎么办呢？通过阅读代码 发现，我们会 skip 掉无效的调用请求。
