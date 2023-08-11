# VueTypeScriptAspNet7.0
visaul studio .17 版本 VueTypeScriptAspNet7.0 

> 嘗試使用預設專案，建立前後端分離專案，並部署至IIS建立服務
>

- node_modules 已刪除，需重新下載

- urlrewrite 請自行放到前臺服務站臺底下

- vueapp 預設使用 vite proxy 加入 changeOrigin: true

- webapi 有自行加入 Cors 設定

- 主要請看：

  - 專案 vueapp >   

    - vite.config.ts
      - 轉址設定
    -  src > components > HelloWorld.vue
      -   頁面

  - 專案 webapi > Program.cs

    - Cros 設定

      ```c#
      //....
      var AllowMyFrontEnd = "AllowMyFrontEnd";
      builder.Services.AddCors(options =>
      {
          options.AddPolicy(name: AllowMyFrontEnd,
          policy =>
          {
              policy.WithOrigins("http://localhost:8095").AllowAnyMethod().AllowAnyHeader();
          });
      });
      
      //....
      app.UseCors(AllowMyFrontEnd);
      ```

  - 前臺目錄 urlrewrite 設定 web.config

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <configuration>
        <system.webServer>
            <rewrite>
                <rules>
                    <rule name="SPA" stopProcessing="true">
                        <match url=".*" />
    					<action type="Rewrite" url="/" />
                        <conditions>
                            <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        </conditions>
                    </rule>
                </rules>
            </rewrite>
        </system.webServer>
    </configuration>
    ```

    
