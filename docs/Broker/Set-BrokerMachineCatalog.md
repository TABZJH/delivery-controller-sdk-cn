# Set-BrokerMachineCatalog

Moves one or more machines into a different catalog.

## 语法

    Set-BrokerMachineCatalog [-InputObject] <Machine[]> [-CatalogUid] <Int32> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerMachineCatalog cmdlet is used to move machines into a different catalog. The following properties of the destination catalog must exactly match those of the machine's current catalog otherwise the command fails:

o AllocationType o ProvisioningType o PersistUserChanges o SessionSupport o IsRemotePC o MinimumFunctionalLevel o PhysicalMachines

Changing a machine's catalog does not change the machine's desktop group membership. There is no effect on user sessions present on a machine if its catalog is changed.

## 相关命令

- [Set-BrokerMachine](Set-BrokerMachine.html)
- [New-BrokerCatalog](New-BrokerCatalog.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The machine instances that are being moved into a different catalog.                                                                                                            | true  | true (ByValue) |                                                                                        |
| CatalogUid   | The unique identifier of the catalog into which the machines are being moved.                                                                                                   | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Machine

You can pipe in the machines that are to be moved into a new catalog.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> $catalog = Get-BrokerCatalog MarketingMachines
              C:\PS> $machines = Get-BrokerMachine -MachineName 'Marketing\*'
              C:\PS> Set-BrokerMachineCatalog $machines -CatalogUid $cat.Uid
    

Description  
\---\---\-----  
This example finds all machines in domain Marketing and moves them into a catalog called MarketingMachines.