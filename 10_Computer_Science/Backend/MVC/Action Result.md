Asp.net MVC5繼承ActionResult抽象類別的回傳型別

|         繼承類別          |                                         Controller方法                                          |         用途         |
| :-------------------: | :-------------------------------------------------------------------------------------------: | :----------------: |
|     ContentResult     |                                           Content()                                           |       回傳文字內容       |
|      ViewResult       |                                            View()                                             |       回傳HTML       |
|      FileResult       |                                            File()                                             |        輸出檔案        |
|  HttpNotFoundResult   |                                        HttpNotFound()                                         | 回應HTTP狀態碼(500、404) |
|      JsonResult       |                                            Json()                                             |       輸出Json       |
|   PartialViewResult   |                                         PartialView()                                         |       部分HTML       |
|    RedirectResult     |                                Redirect();RedirectPermanent()                                 |      重新導向URL       |
| RedirectToRouteResult | RedirectToAction()-RedirectToActionPermanent()-RedirectToRoute()---RedirectToRoutePermanent() |    使用路由，進行URL導向    |


|                    |                  |                    |
| ------------------ | ---------------- | ------------------ |


[ActionResult鐵人賽文章](https://ithelp.ithome.com.tw/articles/10186530)