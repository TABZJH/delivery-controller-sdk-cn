# Remove-BrokerCatalog

Removes catalogs from the site.

## 语法

    Remove-BrokerCatalog [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerCatalog [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove catalogs from the site.

In order to remove a catalog from a site, the catalog must not contain machines. To remove a machine from a catalog use the Remove-BrokerMachine cmdlet. Note: in order to remove a machine from a catalog, it must not belong to a desktop group.

## 相关命令

- [New-BrokerCatalog](New-BrokerCatalog.html)
- [Get-BrokerCatalog](Get-BrokerCatalog.html)
- [Rename-BrokerCatalog](Rename-BrokerCatalog.html)
- [Set-BrokerCatalog](Set-BrokerCatalog.html)
- [New-BrokerDesktopGroup](New-BrokerDesktopGroup.html)
- [Remove-BrokerDesktopGroup](Remove-BrokerDesktopGroup.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the catalog objects to delete.                                                                                                                                        | true  | true (ByValue)        | 空值                                                                                     |
| 名称           | Specifies the name of the catalog to delete.                                                                                                                                    | true  | true (ByPropertyName) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

You can pipe the catalogs to be deleted to Remove-BrokerCatalog.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerCatalog -Name "MyCatalog"
    C:\PS> Remove-BrokerCatalog -InputObject (Get-BrokerCatalog -Name "MyCatalog")
    

Description  
\---\---\-----  
These commands delete the catalog with the name "MyCatalog".

### 示例 2

    C:\PS> Remove-BrokerCatalog -Name 'test*'
    

Description  
\---\---\-----  
This command deletes all catalogs with names beginning with "test".

### 示例 3

    C:\PS> Get-BrokerCatalog -RemotePCDesktopGroupUid 42 | Remove-BrokerCatalog -RemotePCDesktopGroup 42
    

Description  
\---\---\-----  
Remove all the Remote PC catalogs that are associated with desktop group 42. Note that this only breaks the Remote PC relationships and does not delete the desktop groups.