## 思维导航

* [项目介绍](https://github.com)
* [项目特色](https://github.com)
* [项目作用](https://github.com)
* [项目NuGet包](https://github.com)
* [AI服务的常见抽象](https://github.com)
* [参考文章](https://github.com)
* [项目源码地址](https://github.com)
* [优秀项目和框架精选](https://github.com)

## 项目介绍


Microsoft.Extensions.AI是一个创新的 .NET 库，它为平台开发人员提供了一个内聚的 C\# 抽象层，简化了与大型语言模型 （LLMs） 和嵌入等 AI 服务的交互。它支持通过一组一致且标准化的 API 和约定将 AI 功能无缝集成到 .NET 应用程序中。



> 注意：目前`Microsoft.Extensions.AI`还是处于预览版，预计该库将在2024年11月的.NET 9版本之前都是保持预览状态（需要收集反馈意见），耐心等待微软官方发布正式版！


![](https://img2024.cnblogs.com/blog/1336199/202411/1336199-20241117012932915-660709284.png)


## 项目特色


* 统一的API：提供一组一致的 API 和约定，用于将 AI 服务集成到 .NET 应用程序中。
* 灵活性：允许 .NET 库作者使用 AI 服务，而无需绑定到特定提供商，使其适用于任何提供商。
* 易用性：使 .NET 开发人员能够使用相同的底层抽象试验不同的包，并在整个应用程序中维护单个 API。
* 组件化：简化新功能的添加，并促进应用程序的组件化和测试。


:[蓝猫机场](https://fenfang.org)## 项目作用


Microsoft.Extensions.AI类库不仅简化了AI功能的集成，还促进了.NET生态系统的创新。它使得开发者可以更加专注于应用程序的业务逻辑和功能实现，而不必花费大量时间和精力在AI服务的集成和调试上。


## 项目NuGet包


* [https://www.nuget.org/packages/Microsoft.Extensions.AI](https://github.com)


命令安装：



```
dotnet add package Microsoft.Extensions.AI --version 9.0.0-preview.9.24556.5
```

## AI服务的常见抽象


IChatClient 接口允许使用语言模型，无论是远程托管还是本地运行。任何提供 AI 客户端的 .NET 包都可以实现此接口，从而实现与正在使用的 .NET 代码的无缝集成。



```
public interface IChatClient : IDisposable {     Task CompleteAsync(...);     IAsyncEnumerable CompleteStreamingAsync(...);     ChatClientMetadata Metadata { get; }     TService? GetService(object? key = null) where TService : class; } 
```

### OpenAI



```
using OpenAI;using Microsoft.Extensions.AI;IChatClient client =    new OpenAIClient(Environment.GetEnvironmentVariable("OPENAI_API_KEY"))        .AsChatClient(modelId: "gpt-4o-mini");var response = await client.CompleteAsync("C#是什么?");Console.WriteLine(response.Message);
```

### Azure OpenAI



```
using Azure.AI.OpenAI;using Azure.Identity;using Microsoft.Extensions.AI;IChatClient client =    new AzureOpenAIClient(        new Uri(Environment.GetEnvironmentVariable("AZURE_OPENAI_ENDPOINT")),         new DefaultAzureCredential())            .AsChatClient(modelId: "gpt-4o-mini");var response = await client.CompleteAsync("C#是什么?");Console.WriteLine(response.Message);
```

## 参考文章


* [https://devblogs.microsoft.com/dotnet/introducing\-microsoft\-extensions\-ai\-preview](https://github.com)


## 项目源码地址


更多项目实用功能和特性欢迎前往项目开源地址查看👀，别忘了给项目一个Star支持💖。


* 开源地址：[https://github.com/dotnet/extensions](https://github.com)


## 优秀项目和框架精选


该项目已收录到C\#/.NET/.NET Core优秀项目和框架精选中，关注优秀项目和框架精选能让你及时了解C\#、.NET和.NET Core领域的最新动态和最佳实践，提高开发工作效率和质量。坑已挖，欢迎大家踊跃提交PR推荐或自荐（让优秀的项目和框架不被埋没🤞）。


* GitHub开源地址：[https://github.com/YSGStudyHards/DotNetGuide/blob/main/docs/DotNet/DotNetProjectPicks.md](https://github.com)
* Gitee开源地址：[https://gitee.com/ysgdaydayup/DotNetGuide/blob/main/docs/DotNet/DotNetProjectPicks.md](https://github.com)


