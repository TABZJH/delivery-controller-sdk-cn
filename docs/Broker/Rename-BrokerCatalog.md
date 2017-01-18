# Rename-BrokerCatalog

Renames a catalog.

## 语法

    Rename-BrokerCatalog [-InputObject] <Catalog[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-BrokerCatalog [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Rename-BrokerCatalog cmdlet changes the name of a catalog. A catalog cannot have the same name as another catalog.

The following special characters are not allowed in a catalog name: \ / ; : # . * ? = < > | \[ \] ( ) " ' `

## 相关命令

- [Get-BrokerCatalog](Get-BrokerCatalog.html)
- [New-BrokerCatalog](New-BrokerCatalog.html)
- [Remove-BrokerCatalog](Remove-BrokerCatalog.html)
- [Set-BrokerCatalog](Set-BrokerCatalog.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the catalog to rename.                                                                                                                                                | true  | true (ByValue)        |                                                                                        |
| 名称           | Specifies the name of the catalog to rename.                                                                                                                                    | true  | true (ByPropertyName) |                                                                                        |
| NewName      | Specifies the new name of the catalog.                                                                                                                                          | true  | false                 |                                                                                        |
| PassThru     | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

You can pipe catalogs to Rename-BrokerCatalog.

## 返回值

### None or Citrix.Broker.Admin.SDK.Catalog

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Catalog object.

## 示例

### 示例 1

    C:\PS> Rename-BrokerCatalog -Name "Old Name" -NewName "New Name"
    

Description  
\---\---\-----  
Renames the catalog with the name "Old Name" to "New Name".

### 示例 2

    C:\PS> c:\$catalog = Get-BrokerCatalog -Name "Old Name"
    C:\PS> Rename-BrokerCatalog -InputObject $catalog -NewName "New Name"
    

Description  
\---\---\-----  
Renames the catalog with the name "Old Name" to "New Name".