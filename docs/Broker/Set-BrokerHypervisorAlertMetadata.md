# Set-BrokerHypervisorAlertMetadata

Creates/Updates metadata key-value pairs for HypervisorAlert

## 语法

    Set-BrokerHypervisorAlertMetadata [-HypervisorAlertId] <Int64> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerHypervisorAlertMetadata [-HypervisorAlertId] <Int64> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerHypervisorAlertMetadata [-HypervisorAlertId] <Int64> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerHypervisorAlertMetadata [-InputObject] <HypervisorAlert[]> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerHypervisorAlertMetadata [-InputObject] <HypervisorAlert[]> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-BrokerHypervisorAlertMetadata cmdlet creates/updates metadata key-value pairs for HypervisorAlert. The HypervisorAlert can be specified by InputObject or piping.

## 相关命令

## 参数

| 名称                | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| HypervisorAlertId | Specifies the HypervisorAlert object whose Metadata is to be created/updated by ID.                                                                                             | true  | true (ByValue)        |                                                                                        |
| InputObject       | Specifies the HypervisorAlert objects whose Metadata is to be created/updated.                                                                                                  | true  | true (ByValue)        |                                                                                        |
| 名称                | Specifies the name of the Metadata member to be created/updated                                                                                                                 | true  | true (ByPropertyName) |                                                                                        |
| 值                 | Specifies the value of the Metadata member to be created/updated                                                                                                                | true  | true (ByPropertyName) |                                                                                        |
| Map               | Specifies a hashtable containing name/value pairs to be used to create or update Metadata members                                                                               | true  | true (ByValue)        |                                                                                        |
| PassThru          | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                  | false | false                 | False                                                                                  |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress      | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.BrokerHypervisorAlert

You can pipe the HypervisorAlert to hold the new or updated metadata.

## 返回值

### None or Citrix.Broker.Admin.SDK.BrokerHypervisorAlert

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.BrokerHypervisorAlert object.

## 示例

### 示例 1

    C:\PS> Set-BrokerHypervisorAlertMetadata -InputObject $obj-Uid -Name "MyMetadataName" -Value "1234"
    

Description  
\---\---\-----  
This command creates/updates the Metadata "MyMetadataName" key-value pair for the HypervisorAlert whose instance is pointed by $obj-Uid

### 示例 2

    C:\PS> Get-BrokerHypervisorAlert | Set-BrokerHypervisorAlertMetadata -Name "MyMetadataName" -Value "1234"
    

Description  
\---\---\-----  
This command creates/updates metadata key "MyMetadataName" with the value "1234" for all the HypervisorAlert in the site