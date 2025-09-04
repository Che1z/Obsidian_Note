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
