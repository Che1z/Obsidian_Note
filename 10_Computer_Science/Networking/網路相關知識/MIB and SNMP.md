# MIB and SNMP

## MIB (Management Information Base)
MIB 是一種樹狀結構的資料庫，用於管理網路設備中的物件。每個物件代表設備的某個特定資訊，例如 CPU 使用率、記憶體用量或網路介面狀態。

## SNMP (Simple Network Management Protocol)
SNMP 是一個應用層協令，用於在網路管理器和代理程式之間交換管理資訊。它使用 MIB 來識別和組織這些資訊。

---

## 虛擬 Port (Virtual Ports) in MIB

在某些網路設備中，特定的 MIB 物件會對應到虛擬或邏輯上的 Port，而不僅僅是物理介面。

### 範例
- **管理埠 (Management Port)**: 例如 `GigabitEthernet0/0`，雖然它可能是一個物理接口，但在某些情境下被視為一個獨立的管理通道，其狀態和數據會由特定的 MIB 物件來表示。

- **其他虛擬介面**:
  - Loopback interfaces
  - Tunnel interfaces
  - VLAN interfaces (SVI)

要識別哪些 MIB 代表虛擬 Port，通常需要查閱該設備的 MIB 文件或技術手冊。

---

## 網路設備 Port 命名規則

網路設備的 Port（或稱介面）命名通常遵循一個格式，用來標示其物理位置。

### 兩段式命名 (二數字)
這是一種**常見**的命名方式，但非絕對規則。通常用於：
- 獨立、非堆疊的交換器。
- 特定型號設備的管理 Port。

- **格式**: `Type Module/Port`
- **範例**: `GigabitEthernet0/0`
  - `0`: 設備或模組的編號。
  - `0`: 該模組上的 Port 編號。

**注意**: Port 的命名規則完全取決於製造商和設備型號。部分設備擁有完全獨立的帶外 (out-of-band) 管理 Port，其命名可能為 `mgmt0` 或 `ma1`，不遵循數字格式。

### 三段式命名 (三數字)
常見於可堆疊 (stackable) 或模組化 (modular) 的機箱式交換器。
- **格式**: `Type Switch/Module/Port`
- **範例**: `GigabitEthernet1/0/24`
  - `1`: 代表堆疊中的第 1 台交換器 (Switch 1)。
  - `0`: 代表該交換器上的模組編號 (如果設備本身非模組化，通常是 0)。
  - `24`: 代表該模組上的第 24 個 Port。

---

## 設備類型：模組化 vs. 非模組化

這個命名慣例的差異，源自於網路設備的兩種主要設計：

### 非模組化 (Non-modular / Fixed)
- **定義**: 指的是端口數量和類型都是固定的交換器。你無法擴充或更換其端口。
- **外觀**: 通常是單一機架單位 (1U) 的設備。
- **範例**: 一台擁有 48 個固定 Gigabit Ethernet 端口的交換器。
- **命名關聯**: 在 `Switch/Module/Port` 格式中，因為整個設備就是一個單元，沒有可抽換的模組，所以 `Module` 編號通常為 `0`。

### 模組化 (Modular / Chassis-based)
- **定義**: 提供一個空的機箱 (Chassis)，你可以根據需求插入不同的線路卡 (Line Card) 或模組 (Module)。
- **優點**: 具有高度的擴充性、靈活性和備援能力。你可以混合使用不同速度和類型的端口 (如光纖、銅纜)。
- **外觀**: 體積較大，擁有多個插槽 (Slot) 可供模組插入。
- **命名關聯**: `Module` 編號對應到線路卡所插入的插槽編號。例如 `GigabitEthernet1/2/3` 可能指第 1 台交換器、第 2 個插槽上的第 3 個端口。
