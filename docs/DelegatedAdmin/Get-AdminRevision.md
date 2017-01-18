# Get-AdminRevision

Gets the current revision of the delegated administration configuration data.

## 语法

    Get-AdminRevision [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Delegated Administration Service maintains a revision number that is incremented whenever its configuration is changed. This command retrieves the current revision number.

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.Int32

The configuration revision number## Notes If Int32.MaxValue is reached the value of the revision number will wrap around to Int32.MinValue.  
In some cases the value may be incremented by more than one.

## 示例

### 示例 1

    C:\PS> Get-AdminRevision
    

Description  
\---\---\-----  
Retrieve the current revision number.