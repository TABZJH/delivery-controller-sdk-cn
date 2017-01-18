# Remove-ProvSchemeMasterVMImageHistory

Removes the history of provisioning scheme master image VMs.

## 语法

    Remove-ProvSchemeMasterVMImageHistory [-ProvisioningSchemeName] <String> [-VMImageHistoryUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvSchemeMasterVMImageHistory -ProvisioningSchemeUid <Guid> [-VMImageHistoryUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvSchemeMasterVMImageHistory -VMImageHistoryUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to remove the record of previously used master VMs or snapshots for provisioning schemes.

## 相关命令

- [Get-ProvSchemeMasterVMImageHistory](Get-ProvSchemeMasterVMImageHistory.html)
- [Publish-ProvMasterVMImage](Publish-ProvMasterVMImage.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ProvisioningSchemeName | The name of the provisioning scheme.                                                                                                                                   | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeUid  | The unique identifier of the provisioning scheme.                                                                                                                      | true  | false                 |                                       |
| VMImageHistoryUid      | The unique identifier for the Image History item.                                                                                                                      | false | true (ByPropertyName) |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed for  
for various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
ExceptionThrown  
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Remove-ProvSchemeMasterVMImageHistory -ProvisioningSchemeName MyScheme
    

Description  
\---\---\-----  
Removes all history for the provisioning scheme called "MyScheme".

### 示例 2

    c:\PS>Get-ProvScheme | Remove-ProvSchemeMasterVMImageHistory
    

Description  
\---\---\-----  
Removes all history for all provisioning schemes.