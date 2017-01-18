# Remove-AppLibAppDNAConnection

Removes the AppDNA connection.

## 语法

    Remove-AppLibAppDNAConnection [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes the AppDNA connection configuration from Citrix Studio thereby disabling Studio's integration with AppDNA.

## 相关命令

- [Get-AppLibAppDNAConnection](Get-AppLibAppDNAConnection.html)
- [Set-AppLibAppDNAConnection](Set-AppLibAppDNAConnection.html)
- [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)
- [Disable-AppLibAppDNAConnection](Disable-AppLibAppDNAConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### void

## Notes Removing the AppDNA connection will disable any integration Citrix Studio has with AppDNA data.

## 示例

### 示例 1

    C:\PS>Remove-AppLibAppDNAConnection
    

Description  
\---\---\-----  
Removes the AppDNA integration from Citrix Studio