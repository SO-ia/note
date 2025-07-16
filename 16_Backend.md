### Java 项目详解

#### 项目结构

```powershell
D:.
│  .gitattributes
│  .gitignore
│  HELP.md
│  mvnw
│  mvnw.cmd
│  pom.xml
│
├─.idea
│      .gitignore
│      vcs.xml
│      workspace.xml
│
├─.mvn
│  └─wrapper
│          maven-wrapper.properties
│
└─src						# 存放 Java 源码
    ├─main
    │  ├─java
    │  │  └─com.example.legal
    │  │        Application.java
    │  │
    │  └─resources
    │      │  application.properties
    │      │
    │      ├─static
    │      └─templates
    └─test
        └─java
            └─com.example.legal
                 ApplicationTests.java

```

```java
/**
 * 接受前端请求，并将请求转发给服务层调用模型对话
 */
package com.example.legal.controller;


import com.example.legal.service.ChatService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;


// 注解说明
// 说明该类是一个 Restful 控制器，用于处理 HTTP 请求
@RestController
// 指定该控制器的根路径为 /api
@RequestMapping("/api")
public class ChatController {

    @Autowired
    private ChatService chatService;

    // 该方法用于处理 /chat 的 POST 请求
    @PostMapping("/chat")
    // @RequestBody 用于将请求体中的 JSON 数据绑定到方法参数中
    public String chat(@RequestBody String message) {
        return chatService.getModelResponse(message);
    }
}

```



```java
/**
 * 处理具体的业务逻辑，调用模型对话接口
 */

package com.example.legal.service;


import org.springframework.beans.factory.annotation.Value;
import org.springframework.http.*;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestTemplate;


// 表示一个服务组件，用于处理业务逻辑
@Service
public class ChatService {
    // 从 application.properties 文件中读取模型接口地址
    @Value("${model.api.url}")
    private String apiUrl;

    public String getModelResponse(String message){
        try {
            // RestTemplate：Spring 用于发送 HTTP 请求的工具类
            RestTemplate restTemplate = new RestTemplate();
            // 设置请求头信息，如内容类型
            HttpHeaders headers = new HttpHeaders();

            headers.setContentType(MediaType.APPLICATION_JSON);
            // 封装请求体和请求头
            HttpEntity<String> entity = new HttpEntity<>(message, headers);
            // restTemplate.exchange()方法: 发送 HTTP 请求并获取响应结果
            // ResponseEntity 表示 HTTP 响应，包含响应体、状态码等信息
            ResponseEntity<String> responseEntity = restTemplate.exchange(apiUrl, HttpMethod.POST, entity, String.class);
            return responseEntity.getBody();
        } catch (Exception e) {
            return "模型调用失败: " + e.getMessage();
        }
    }
}

```



> https://blog.csdn.net/mng123/article/details/146760861



#### Maven

- 跨平台的项目管理工具
- 管理Java: 项目创建、依赖管理、项目信息管理
  - 相当于 anaconda ？

##### maven 清理教程

https://cloud.tencent.com/developer/article/2056371



#### JDK



##### 删除重复 JDK

file — project structure — SDKs

https://blog.csdn.net/m0_57320261/article/details/147341245



### error

#### 1 IDE

```powershell
The IDE has detected Microsoft Defender with Real-Time Protection enabled. It might severely degrade IDE performance. It is recommended to add the following paths to the Defender folder exclusion list:    C:\Users\HUAWEI\AppData\Local\JetBrains\IntelliJIdea2024.2   D:\A_assignment\work\C_Java\002_NoSQL\Redis_MySQL_web  Choose "Automatically" to run a script that excludes these paths (note: Windows will ask for administrative privileges). Choose "Manually" to see Defender configuration instructions.
```

windows security ==> Virus & threat protection ==> Virus & threat protection settings ==> Manage settings ==> Exclusions ==> Add or remove exclusions

> https://blog.csdn.net/superherowupan/article/details/143286542





```java
@RestController
@RequestMapping("/api")
public class ChatController {
    @PostMapping("/chat")
    public String chat(@RequestBody String message) {
        // 调用模型接口
        return modelResponse(message);
    }

    private String modelResponse(String message) {
        // 调用模型接口，这里使用 FastAPI 的接口
        // 实际项目中需替换为真实的模型接口地址
        return "模型返回：" + message;
    }
}
```



#### 2 dependency

##### 页面 404

控制台返回正常

```powershell
2025-06-18T23:22:08.006+08:00  INFO 13192 --- [001_legal] [nio-8080-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring DispatcherServlet 'dispatcherServlet'
2025-06-18T23:22:08.006+08:00  INFO 13192 --- [001_legal] [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Initializing Servlet 'dispatcherServlet'
2025-06-18T23:22:08.007+08:00  INFO 13192 --- [001_legal] [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Completed initialization in 1 ms
```

忘记引入 maven 依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

