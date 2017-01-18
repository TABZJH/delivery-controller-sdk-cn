# Set-BrokerCatalog

Sets the properties of a catalog.

## 语法

    Set-BrokerCatalog [-InputObject] <Catalog[]> [-PassThru] [-Description <String>] [-IsRemotePC <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-ProvisioningSchemeId <Guid>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerCatalog [-Name] <String> [-PassThru] [-Description <String>] [-IsRemotePC <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-ProvisioningSchemeId <Guid>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerCatalog cmdlet sets properties of a catalog or set of catalogs. The catalog can be specified by name, in which case only one catalog can be specified, or one or more catalog instances can be passed to the command either by piping or by using the -InputObject parameter.

## 相关命令

- [Get-BrokerCatalog](Get-BrokerCatalog.html)
- [New-BrokerCatalog](New-BrokerCatalog.html)
- [Remove-BrokerCatalog](Remove-BrokerCatalog.html)
- [Rename-BrokerCatalog](Rename-BrokerCatalog.html)

## 参数

| 名称                              | 说明                                                                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject                     | Specifies the catalog objects to modify.                                                                                                                                                                                                                                                                                              | true  | true (ByValue)        |                                                                                        |
| 名称                              | Identifies the catalog to modify.                                                                                                                                                                                                                                                                                                     | true  | true (ByPropertyName) |                                                                                        |
| PassThru                        | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                                                                        | false | false                 | False                                                                                  |
| 说明                              | Supplies the new value of the Description property.                                                                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| IsRemotePC                      | Supplies a new value for IsRemotePC.  
IsRemotePC can only be enabled when:  
o SessionSupport is SingleSession  
o MachinesArePhysical is true.  
IsRemotePC can only be set from true to false when no RemotePCAccount references this catalog, and when no Remote PC relationship exists between this catalog and a desktop group. | false | false                 |                                                                                        |
| MinimumFunctionalLevel          | The new minimum FunctionalLevel required for machines to work successfully in the catalog. If this is higher than the FunctionalLevel of any machines already in the catalog, they will immediately cease to function.  
Valid values are L5, L7, L7_6                                                                                | false | false                 |                                                                                        |
| ProvisioningSchemeId            | Specifies the identity of the MCS provisioning scheme the catalog is associated with (can only be specified for new catalogs with a ProvisioningType of MCS; once set can never be changed).                                                                                                                                          | false | false                 |                                                                                        |
| PvsAddress                      | Supplies the new value of the PvsAddress property. Can only be set if CatalogKind is Pvs or PvsPvd.                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| PvsDomain                       | Supplies the new value of the PvsDomain property. Can only be set if CatalogKind is PvsPvd.                                                                                                                                                                                                                                           | false | false                 |                                                                                        |
| RemotePCHypervisorConnectionUid | Supplies the new hypervisor connection to use for powering on remote PCs in this catalog (only allowed when IsRemotePC is true); this will affect all machines already in the catalog as well as those created later.                                                                                                                 | false | false                 |                                                                                        |
| ZoneUid                         | Supplies the Zone Uid associated with this catalog.                                                                                                                                                                                                                                                                                   | false | false                 |                                                                                        |
| LoggingId                       | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                       | false | false                 |                                                                                        |
| AdminAddress                    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                    | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

You can pipe the catalogs to be modified to Set-BrokerCatalog.

## 返回值

### None or Citrix.Broker.Admin.SDK.Catalog

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Catalog object.## Notes A catalog's Name property cannot be changed by Set-BrokerCatalog. To rename a catalog use Rename-BrokerCatalog.

## 示例

### 示例 1

    C:\PS> Set-BrokerCatalog -Name "MyCatalog" -Description "New Description"
    

Description  
\---\---\-----  
This example specifies a catalog by name and sets its description.

### 示例 2

    C:\PS> $permCatalogs = Get-BrokerCatalog -AllocationType Static
    C:\PS> Set-BrokerCatalog -InputObject $permCatalogs -Description "Permanently assigned machines"
    

Description  
\---\---\-----  
This example sets the description for all catalogs with AllocationType 'Static'.