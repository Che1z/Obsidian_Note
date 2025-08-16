dll是c#檔案編譯過後檔案類型
.cs --> .dll (透過compilation)

## 什麼是 DLL？ (What is a DLL?)

DLL 的全名是 **Dynamic Link Library (動態連結程式庫)**。

它是一個包含可由多個程式同時使用之程式碼和資料的程式庫。簡單來說，你可以把一組可重複使用的程式碼（例如一些共用的函式、類別）編譯成一個 DLL 檔案，然後讓你的主程式或其他專案來呼叫使用這些功能。

.cs 原始碼檔案經過編譯 (compilation) 後，可以產生成兩種主要的檔案類型：
1.  **.dll (Dynamic Link Library):** 類別庫。它不能自行執行，必須由其他應用程式（如 .exe 或其他 .dll）來呼叫。
2.  **.exe (Executable):** 可執行檔。這是應用程式的主要進入點，可以獨立執行。

## 為什麼要使用 DLL？ (Why use DLLs?)

使用 DLL 有許多好處：

*   **程式碼重複使用 (Code Reusability):** 多個專案可以共用同一個 DLL，不需重複撰寫相同的程式碼。
*   **模組化 (Modularity):** 可以將大型應用程式拆分成多個獨立的模組（DLLs），讓開發和維護更加容易。例如，一個模組負責資料庫存取，另一個負責使用者介面。
*   **簡化部署與更新 (Simplified Deployment and Updates):** 當你只需要更新某個模odule的功能時，你只需要替換對應的 DLL 檔案，而不用重新編譯和部署整個應用程式。
*   **節省記憶體 (Saves Memory):** 當多個程式使用同一個 DLL 時，作業系統可以在記憶體中只載入一份 DLL，供所有程式共用，從而節省資源。

## DLL 在 .NET 中的角色：組件 (Assembly)

在 .NET 的世界裡，DLL 和 EXE 都被稱為 **組件 (Assembly)**。

組件是 .NET 應用程式的基本建置組塊，是部署、版本控制、權限管理和程式碼重複使用的基本單位。每個組件都包含著中繼資料 (Metadata)，用來描述組件本身，以及它所包含的型別（classes, interfaces, etc.）。

當你建立一個 C# 的類別庫 (Class Library) 專案時，編譯後的產出就是一個 DLL 組件。

## 如何使用？ (How to use it?)

典型的流程如下：

1.  **建立類別庫專案:** 在 Visual Studio 中建立一個 "Class Library" 專案，並在其中撰寫你的共用程式碼。
2.  **編譯專案:** 編譯這個專案，就會在 `bin/Debug` 或 `bin/Release` 資料夾下產生一個 .dll 檔案。
3.  **參考 DLL:** 在你的主應用程式專案（例如一個 Console App 或 Web App）中，加入對這個 DLL 檔案的參考 (Reference)。
4.  **使用功能:** 加入參考後，你就可以像使用內建的類別一樣，在你的主程式中 `using` 該 DLL 的命名空間，並使用其中定義的公開 (public) 類別和方法。
