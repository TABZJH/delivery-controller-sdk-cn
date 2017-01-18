# Get-BrokerConfiguredFTA

Gets any file type associations configured for an application.

## 语法

    Get-BrokerConfiguredFTA -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerConfiguredFTA [-ApplicationUid <Int32>] [-ContentType <String>] [-ExtensionName <String>] [-HandlerDescription <String>] [-HandlerName <String>] [-HandlerOpenArguments <String>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets any file type associations that are configured for content redirection to a published application.

File type association associates a file extension (such as ".txt") with an application (such as Notepad). In a Citrix environment file type associations on a user device can be configured so that when an user clicks on a document it launches the appropriate published application. This is known as "content redirection".

Configured file type associations are different from imported file type associations. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection. Imported file type associations are lists of known file type associations for a given desktop group. See Update-BrokerImportedFTA for more information about imported file type associations.

\---\---\---\---\---\---\---\----- BrokerConfiguredFTA Object The BrokerConfiguredFTA object represents a file type association configured for a published application. It contains the following properties:

    -- ApplicationUid (System.Int32)
       The Uid of the application configured for the file type association.
    
    -- ContentType (System.String)
       Content type of the file, such as "text/plain" or "application/vnd.ms-excel".
    
    -- ExtensionName (System.String)
       A single file extension, such as .txt, unique within the scope of a desktop group.
    
    -- HandlerDescription (System.String)
       File type description, such as "Test Document", "Microsoft Word Text Document", etc.
    
    -- HandlerName (System.String)
       File type handler name, e.g. "Word.Document.8" or TXTFILE.
    
    -- HandlerOpenArguments (System.String)
       The arguments used for the ‘open’ action on files of this type.
    
    -- Uid (System.Int32)
       Unique internal identifier of configured file type association.
    
    -- UUID (System.Guid)
       UUID of the configured file type association.
    

## 相关命令

- [New-BrokerConfiguredFTA](New-BrokerConfiguredFTA.html)
- [Remove-BrokerConfiguredFTA](Remove-BrokerConfiguredFTA.html)
- [Update-BrokerImportedFTA](Update-BrokerImportedFTA.html)

## 参数

| 名称                     | 说明                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets only the configured file type association for the specified unique identifier.                                                                                              | true  | false |                                                                                        |
| ApplicationUid         | Gets only the configured file type associations for the specified application unique identifier.                                                                                 | false | false |                                                                                        |
| ContentType            | Gets only the configured file type associations for the specified content type (as seen in the Registry). For example, "text/plain" or "application/msword".                     | false | false |                                                                                        |
| ExtensionName          | Gets only the configured file type associations for the specified extension name. For example, ".txt" or ".doc".                                                                 | false | false |                                                                                        |
| HandlerDescription     | Gets only the configured file type associations for the specified handler description. For example, "Text Document".                                                             | false | false |                                                                                        |
| HandlerName            | Gets only the configured file type associations for the specified handler name. For example, "TXTFILE" or "Word.Document.8".                                                     | false | false |                                                                                        |
| HandlerOpenArguments   | Gets only the configured file type associations for the specified open argument to the handler. For example, "%1".                                                               | false | false |                                                                                        |
| UUID                   | Gets configured file type associations with the specified value of UUID.                                                                                                         | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details. | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                     | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                            | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                         | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                          | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                           | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                               | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

No input is accepted from the pipeline.

## 返回值

### Citrix.Broker.Admin.SDK.ConfiguredFTA

This cmdlet returns one or more ConfiguredFTA objects.

## 示例

### 示例 1

    C:\PS> Get-BrokerConfiguredFTA
    

Description  
\---\---\-----  
Returns all configured file type associations.

### 示例 2

    C:\PS> Get-BrokerConfiguredFTA -ExtensionName ".txt"
    

Description  
\---\---\-----  
Returns only configured file type associations that have a ".txt" extension.