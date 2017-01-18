# Remove-ConfigServiceGroup

Removes service groups.

## 语法

    Remove-ConfigServiceGroup [-ServiceGroupUid] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to remove a service group and all the service instances that it contains.

## 相关命令

- [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
- [Add-ConfigServiceGroupMetadata](Add-ConfigServiceGroupMetadata.html)
- [Set-ConfigServiceGroupMetadata](Set-ConfigServiceGroupMetadata.html)
- [Remove-ConfigServiceGroupMetadata](Remove-ConfigServiceGroupMetadata.html)

## 参数

| 名称              | 说明                                                                                      | 是否必需？ | 管道输入                  | 默认值                                   |
| --------------- | --------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ServiceGroupUid | The unique identifier for the service group.                                            | true  | true (ByPropertyName) |                                       |
| LoggingId       | Specifies the logging id of the high-level operation this cmdlet invocation is part of. | false | false                 |                                       |
| AdminAddress    | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                               | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes \---\---\----- ServiceGroupObjectNotFound The service group specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS>Remove-ConfigServiceGroup -ServiceGroupUid 31951f6f-7703-4abb-938a-2861d76ecfea
    

Description  
\---\---\-----  
Removes the service group (and all contained service instances) for the service group with a unique identifier of '31951f6f-7703-4abb-938a-2861d76ecfea'.

### 示例 2

    C:\PS> Get-ConfigServiceGroup | Remove-ConfigServiceGroup
    

Description  
\---\---\-----  
Removes all the service groups (and all contained service instances) for the XenDesktop deployment.