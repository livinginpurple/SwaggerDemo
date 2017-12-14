# SwaggerDemo

## C# MVC Web Api Swagger Installation Settings 安裝設定

## 環境

+ Visual Studio 2015
+ Windows 7
+ .Net Framework 4.6.2

## 開新專案

若未使用 Application Insights，不勾選。
![開新專案](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-01.png)

## 選擇專案類型 (Web API)

選擇 Web API，並使用 No Authentication (若未使用任何認證方式)
![選擇專案類型 (Web API)](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-02.png)

![選擇 No Authentication](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-03.png)

## 專案名稱為：WebApplicationSwagger

![WebApplicationSwagger](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-04.png)

## 安裝 Swashbuckle

1. 透過 Nuget GUI 安裝

![Swashbuckle Installation 1](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-05.png)

2. 透過 Package Manager Console 安裝，安裝指令：

```
Install-Package Swashbuckle
```

![Swashbuckle Installation 2](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-06.png)

3. 安裝前後差異

![Swashbuckle Installation 3](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-08.png)

+ +Swashbuckle
+ +Swashbuckle.Core
+ +WebActivatorEx
+ Newtonsoft.Json version="7.0.1"

![Swashbuckle Installation 4](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-09.png)

## Api XML 文件設定

預設設定

![XML Settings 1](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-10.png)

選擇XML文件產出路徑，這邊設定為「bin\WebApplicationSwagger.XML」

![XML Settings 2](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-11.png)

修改 Property 後，顯示已修改過

![XML Settings 3](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-12.png)

## App_Start\SwaggerConfig.cs 設定

EnableSwagger，設定 XML 路徑
![Swagger Settings 1](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-13.png)

路徑設定錯誤，顯示找不到檔案

![Swagger Settings 2](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-14.png)

```cs
c.IncludeXmlComments(GetXmlCommentsPath());
```

![Swagger Settings 3](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-16.png)

### 路徑設定正確，顯示 Swagger 頁面

```cs
        private static string GetXmlCommentsPath()
        {
            return System.IO.Path.Combine(AppDomain.CurrentDomain.BaseDirectory, @"bin\WebApplicationSwagger.XML");
        }
```

![Swagger Settings 4](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-15.png)

網址為：http://localhost:{Port}/swagger

![Swagger Settings 5](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-17.png)

EnableSwaggerUi，設定自訂範本 index.html

[範本下載](
https://github.com/domaindrivendev/Swashbuckle/blob/master/Swashbuckle.Core/SwaggerUi/CustomAssets/index.html)

![Swagger Settings 6](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-18.png)

![Swagger Settings 7](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-19.png)

正確路徑：

```cs
c.CustomAsset("index", typeof(SwaggerConfig).Assembly, "專案名稱.Content.index.html");
```

![Swagger Settings 8](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-20.png)

路徑錯誤，顯示找不到 Embedded Resource：

![Swagger Settings 9](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-21.png)

![Swagger Settings 10](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-22.png)

設定 Content/index.html Property 為 Embedded Resource

![Swagger Settings 11](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-23.png)

路徑設定正確

![Swagger Settings 12](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-24.png)

### 自訂 Swagger 頁面 Html Title

```cs
c.DocumentTitle("My Swagger UI");
```

![Swagger Settings 13](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-25.png)

![Swagger Settings 14](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-26.png)

### 自訂 Swagger 頁面，預設顯示 API 清單

```cs
c.DocExpansion(DocExpansion.List);
```

![Swagger Settings 15](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-27.png)

![Swagger Settings 16](https://raw.githubusercontent.com/livinginpurple/SwaggerDemo/master/Images/Swagger-28.png)