# Get-BrokerSessionPreLaunch

Gets one or more session pre-launch settings.

## 语法

    Get-BrokerSessionPreLaunch [-DesktopGroupUid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerSessionPreLaunch [[-DesktopGroupName] <String>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserUPN <String>] [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-UserSID <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerSessionPreLaunch cmdlet is used to enumerate desktop group session pre-launch settings that match all of the supplied criteria.

Without parameters, Get-BrokerSessionPreLaunch gets all the session pre-launch settings that have been created. You can also use the parameters of Get-BrokerSessionPreLaunch to filter the results to just the desktop group you're interested in.

Note that each desktop group can only have a single session pre-launch setting. Session pre-launch only applies to application sessions.

See about_Broker_Filtering for information about advanced filtering options.

\---\---\---\---\---\---\---\----- BrokerSessionPreLaunch Object The session pre-launch object returned represents a session pre-launch setting in a desktop group.

    -- AssociatedUserFullNames (System.String[])
       List of associated users (full names). Associated users is the list of users who are given access using the pre-launch/user mapping filter.
    
    -- AssociatedUserNames (System.String[])
       List of associated users (SAM names). Associated users is the list of users who are given access using the pre-launch/user mapping filter.
    
    -- AssociatedUserUPNs (System.String[])
       List of associated users (user principle names). Associated users is the list of users who are given access using the pre-launch/user mapping filter.
    
    -- DesktopGroupName (System.String)
       Name of the associated desktop group.
    
    -- DesktopGroupUid (System.Int32)
       Uid of the associated desktop group.
    
    -- Enabled (System.Boolean)
       Specifies whether or not session pre-launch is enabled for the desktop group.
    
    -- MaxAverageLoadThreshold (System.Int32)
       Specifies the average load threshold across the desktop group. After this threshold is hit pre-launched sessions will be terminated to reduce average load across the group. Sessions that have been pre-launched the longest will be chosen first.
    
    -- MaxLoadPerMachineThreshold (System.Int32)
       Specifies the maximum load threshold per machine in the desktop group. After this threshold is hit pre-launched sessions on loaded machines will be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first.
    
    -- MaxTimeBeforeDisconnect (System.TimeSpan)
       Specifies the maximum time by when a pre-launched session will be disconnected. The disconnect timer cannot be greater than the terminate timer. When the disconnect timer is same as the terminate timer, the session will be directly be terminated. The default value is 15 minutes. A value of 0 disables the disconnect timer.
    
    -- MaxTimeBeforeTerminate (System.TimeSpan)
       Specifies the maximum time by when a pre-launched session will be terminated. When the disconnect timer is same as the terminate timer, the session will be directly be terminated. The default value is 8 hours. A value of 0 disables the terminate timer.
    
    -- UserFilterEnabled (System.Boolean)
       Indicates if pre-launch-specific user filter is enabled.
    

## 相关命令

- [New-BrokerSessionPreLaunch](New-BrokerSessionPreLaunch.html)
- [Set-BrokerSessionPreLaunch](Set-BrokerSessionPreLaunch.html)
- [Remove-BrokerSessionPreLaunch](Remove-BrokerSessionPreLaunch.html)

## 参数

| 名称                         | 说明                                                                                                                                                                                                                                                                                                                              | 是否必需？ | 管道输入  | 默认值                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DesktopGroupUid            | Gets session pre-launch setting that is associated with the specified desktop group Uid.                                                                                                                                                                                                                                        | true  | false |                                                                                        |
| DesktopGroupName           | Gets session pre-launch setting that is associated with the specified desktop group name.                                                                                                                                                                                                                                       | false | false |                                                                                        |
| AssociatedUserFullName     | Gets session pre-launch settings with an associated user identified by their full name (usually 'first-name last-name'). If the ‘UserFilterEnabled’ property is true then access to the session pre-launch is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules).      | false | false |                                                                                        |
| AssociatedUserName         | Gets session pre-launch settings with an associated user identified by their user name (in the form 'domain\user'). If the ‘UserFilterEnabled’ property is true then access to the session pre-launch is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules).          | false | false |                                                                                        |
| AssociatedUserUPN          | Gets session pre-launch settings with an associated user identified by their user principle name (in the form 'user@domain'). If the ‘UserFilterEnabled’ property is true then access to the session pre-launch is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |                                                                                        |
| 已启用                        | Gets only the session pre-launch settings that have the specified value for whether the setting is enabled.                                                                                                                                                                                                                     | false | false |                                                                                        |
| MaxAverageLoadThreshold    | Gets only the session pre-launch settings that have the specified average load threshold.                                                                                                                                                                                                                                       | false | false |                                                                                        |
| MaxLoadPerMachineThreshold | Gets only the session pre-launch settings that have the specified maximum load threshold per machine.                                                                                                                                                                                                                           | false | false |                                                                                        |
| MaxTimeBeforeDisconnect    | Gets only the session pre-launch settings that have the specified idle disconnect time.                                                                                                                                                                                                                                         | false | false |                                                                                        |
| MaxTimeBeforeTerminate     | Gets only the session pre-launch settings that have the specified idle terminate time.                                                                                                                                                                                                                                          | false | false |                                                                                        |
| UserFilterEnabled          | Gets only session pre-launch settings whose user filter is in the specified state.                                                                                                                                                                                                                                              | false | false |                                                                                        |
| UserSID                    | Gets only session pre-launch settings with their accessibility restricted to include the specified user.                                                                                                                                                                                                                        | false | false |                                                                                        |
| ReturnTotalRecordCount     | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                                                                                                                                | false | false | False                                                                                  |
| MaxRecordCount             | 指定要返回的最大记录数。                                                                                                                                                                                                                                                                                                                    | false | false | 250                                                                                    |
| 跳过                         | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                                                                                                                           | false | false |                                                                                        |
| SortBy                     | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                                                                                                                        | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                        | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                                                                                                                         | false | false |                                                                                        |
| 属性                         | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                                                                                                                          | false | false |                                                                                        |
| AdminAddress               | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                              | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.SessionPreLaunch

Get-BrokerSessionPreLaunch returns an object for each session pre-launch setting it gets.

## 示例

### 示例 1

    C:\PS> Get-BrokerSessionPreLaunch -DesktopGroupName "test"
    

Description  
\---\---\-----  
Returns the session pre-launch settings associated with the destkop group named 'test'.