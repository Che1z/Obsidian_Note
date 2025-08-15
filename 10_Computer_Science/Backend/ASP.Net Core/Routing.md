**Routing** 就是在 ASP.NET Core 中處理 HTTP 請求的一個「配對過程」，目的是根據 **HTTP 方法**（例如 GET、POST 等）和 **URL**（路徑）來將請求導向到相應的 **Endpoint**。

過程步驟如下：

1. **接收請求**：當應用程式接收到一個 HTTP 請求時，ASP.NET Core 會先經過 Middleware 管道，直到到達 **Routing Middleware**。
    
2. **匹配路由**：Routing Middleware 會使用一組已定義的路由規則來解析請求的 URL 路徑和 HTTP 方法。這些路由規則通常在程式碼中定義，例如在 `Startup.cs` 中使用 `app.UseEndpoints`，或在 MVC 控制器中使用 `[Route]` 屬性來設定。
    
3. **尋找對應的 Endpoint**：Routing Middleware 會根據請求的 URL 路徑和 HTTP 方法，查找是否有符合的 Endpoint。如果找到相應的 Endpoint，請求就會被傳送到該 Endpoint 進行處理；如果找不到匹配的路由，則會回傳一個 404 Not Found 的錯誤。
    
4. **執行 Endpoint**：一旦配對成功，該請求將進入對應的 Endpoint（例如一個控制器方法或 Razor Page 的處理邏輯），執行相關業務邏輯，並生成回應。