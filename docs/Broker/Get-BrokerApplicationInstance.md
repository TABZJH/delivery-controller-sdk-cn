# Get-BrokerApplicationInstance

Gets the running applications on the desktops.

## 语法

    Get-BrokerApplicationInstance -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerApplicationInstance [-ApplicationName <String>] [-ApplicationUid <Int32>] [-ApplicationUUID <Guid>] [-Instances <Int32>] [-MachineName <String>] [-MachineUid <Int32>] [-Metadata <String>] [-SessionKey <Guid>] [-SessionUid <Int64>] [-UserName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerApplicationInstance gets the published applications that are running on desktops.

Only published applications that are launched from a Citrix client are returned. If a user launches an application from within a session (by double-clicking on an attachment from an email, for example) this will not show up in the list of running applications.

Also note that this is a list of launched published applications, not a list of processes running on the desktop. In some cases the original process associated with the published application may no longer be running, but if the session is still running the published application may be listed as running.

The number of instances for each published application running in a session is also returned. For example, if a user launches two Notepad applications from a Citrix client, and session-sharing occurs such that both Notepad applications run in the same session, then the Instances property indicates that 2 copies are running in the session.

See Get-BrokerApplication and Get-BrokerSession to get the details for the applications and sessions, respectively.

The Get-BrokerMachine cmdlet also returns a list of published applications that are running on a desktop. See the "ApplicationsInUse" attribute of the returned desktop objects.

\---\---\---\---\---\---\---\----- BrokerApplicationInstance Object The BrokerApplicationInstance object represents an instance of a published application in the site. It contains the following properties:

    -- ApplicationName (System.String)
       The administrative name of the application.
    
    -- ApplicationUid (System.Int32)
       The UID of the application.
    
    -- ApplicationUUID (System.Guid)
       The UUID of the application.
    
    -- Instances (System.Int32)
       The number of times this published application is running in the specified session.
    
    -- MachineName (System.String)
       Machine's SAM name (of the form domain\machine). If SAM name is unavailable, contains the machines's SID.
    
    -- MachineUid (System.Int32)
       UID of underlying machine.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this application instance.
    
    -- SessionKey (System.Guid)
       The key of the session.
    
    -- SessionUid (System.Int64)
       The UID of the session.
    
    -- Uid (System.Int64)
       The unique identifier for this application instance object itself, distinct from the Uids of either application or session. objects.
    
    -- UserName (System.String)
       User name (SAMName).
    

## 相关命令

- [Get-BrokerApplication](Get-BrokerApplication.html)
- [Get-BrokerDesktop](Get-BrokerDesktop.html)
- [Get-BrokerSession](Get-BrokerSession.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                        | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                    | Gets only the application instances specified by the unique identifier. This is the unique identifier for the application instance object itself, and is distinct from the Uids of either application or session objects. | true  | false |                                                                                        |
| ApplicationName        | Gets only application instances for the specified application name.                                                                                                                                                       | false | false |                                                                                        |
| ApplicationUid         | Gets only application instances for the specified application Uid.                                                                                                                                                        | false | false |                                                                                        |
| ApplicationUUID        | Gets only the application instances for the specified application UUID.                                                                                                                                                   | false | false |                                                                                        |
| Instances（实例）          | Gets only application instances that match the specified number of instances.                                                                                                                                             | false | false |                                                                                        |
| MachineName            | Gets only application instances running on the specified machines.                                                                                                                                                        | false | false |                                                                                        |
| MachineUid             | Gets only application instances running on the machine with the specified UID.                                                                                                                                            | false | false |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                                 | false | false |                                                                                        |
| SessionKey             | Gets only application instances for the published applications running in the specified session.                                                                                                                          | false | false |                                                                                        |
| SessionUid             | Gets only application instances for the published applications running in the specified session.                                                                                                                          | false | false |                                                                                        |
| 用户名                    | Gets only application instances being run by the specified users.                                                                                                                                                         | false | false |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                          | false | false | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                                              | false | false | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                     | false | false |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                  | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                   | false | false |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                    | false | false |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                        | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.ApplicationInstance

Get-BrokerApplicationInstance returns an object for each application instance it gets.

## 示例

### 示例 1

    C:\PS> Get-BrokerApplicationInstance -Uid 3
    

Description  
\---\---\-----  
Returns the application instance with a Uid of 3. Note that this is the unique identifier for application instances, which is distinct from the unique identifiers of either application or session objects.

### 示例 2

    C:\PS> $app = Get-BrokerApplication Notepad
    C:\PS> Get-BrokerApplicationInstance -ApplicationUid $app.Uid
    

Description  
\---\---\-----  
Returns all the application instances for the Notepad application. Use this to see if there are any launched instances of Notepad running in your site and, if so, from which desktops.

### 示例 3

    C:\PS> $sessions = Get-BrokerSession -MachineName "ACME\Worker1"
    C:\PS> for ($i=0; $i -lt $sessions.Length; $i++) {
                Get-BrokerApplicationInstance -SessionUid $sessions[$i].SessionUid
              }
    

Description  
\---\---\-----  
Returns all the applications that are running on the "Worker1" machine in the "ACME" domain. Use this to see which published applications are running on a specific machine.  
Note that the SessionUid, not the SessionId, is specified as a parameter to this cmdlet. The SessionId is a unique identifier that Remote Desktop Services uses to track the session, and is unique only on that machine. The SessionUid, on the other hand, is unique across the entire site.  
The "ApplicationsInUse" attribute of the returned session object also provides a list of running launched applications, and in many cases might be more convenient to use. It returns a list of application BrowserNames.