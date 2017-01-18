# Get-BrokerApplication

Get the applications published on this site.

## 语法

    Get-BrokerApplication [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerApplication [[-Name] <String>] [-AdminFolderName <String>] [-AdminFolderUid <Int32>] [-AllAssociatedDesktopGroupUid <Int32>] [-AllAssociatedDesktopGroupUUID <Guid>] [-ApplicationName <String>] [-ApplicationType <ApplicationType>] [-AssociatedApplicationGroupUid <Int32>] [-AssociatedApplicationGroupUUID <Guid>] [-AssociatedDesktopGroupPriority <Int32>] [-AssociatedDesktopGroupUid <Int32>] [-AssociatedDesktopGroupUUID <Guid>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserUPN <String>] [-BrowserName <String>] [-ClientFolder <String>] [-CommandLineArguments <String>] [-CommandLineExecutable <String>] [-CpuPriorityLevel <CpuPriorityLevel>] [-Description <String>] [-Enabled <Boolean>] [-HomeZoneName <String>] [-HomeZoneOnly <Boolean>] [-HomeZoneUid <Guid>] [-IconFromClient <Boolean>] [-IconUid <Int32>] [-IgnoreUserHomeZone <Boolean>] [-MaxPerUserInstances <Int32>] [-MaxTotalInstances <Int32>] [-MetadataKey <String>] [-Metadata <String>] [-PublishedName <String>] [-SecureCmdLineArgumentsEnabled <Boolean>] [-ShortcutAddedToDesktop <Boolean>] [-ShortcutAddedToStartMenu <Boolean>] [-StartMenuFolder <String>] [-Tag <String>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-Visible <Boolean>] [-WaitForPrinterCreation <Boolean>] [-WorkingDirectory <String>] [-DesktopUid <Int32>] [-ApplicationGroupUid <Int32>] [-SessionUid <Int64>] [-UserSID <String>] [-DesktopGroupUid <Int32>] [-MachineConfigurationUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-BrokerApplication cmdlet gets the published applications that are hosted on this site.

Without parameters, Get-BrokerApplication gets all the applications that have been published, regardless of whether they are visible to users or not. You can also use the parameters of Get-BrokerApplication to filter the results to just the applications you're interested in. You can also identify applications by their UIDs or their BrowserNames.

For more information about applications, see about_Broker_Applications.

\---\---\---\---\---\---\---\----- BrokerApplication Object The BrokerApplication object represents a published application in the site. It contains the following properties:

    -- AdminFolderName (System.String)
       The name of the admin folder the application is in (including trailing backslash), or the empty string if the application is at the root level
    
    -- AdminFolderUid (System.Int32)
       The Uid of the admin folder the application is in (if any)
    
    -- AllAssociatedDesktopGroupUids (System.Int32[])
       List of associated desktop group uids, including desktop groups that are indirectly associated with the application by virtue of being associated with an application group of which this application is a member.
    
    -- AllAssociatedDesktopGroupUUIDs (System.Guid[])
       List of associated desktop group UUIDs, including desktop groups that are indirectly associated with the application by virtue of being associated with an application group of which this application is a member.
    
    -- ApplicationName (System.String)
       The simple name of the application within its parent admin folder (if any)
    
    -- ApplicationType (Citrix.Broker.Admin.SDK.ApplicationType)
       The type of the application, whether HostedOnDesktop, InstalledOnClient or PublishedContent.
    
    -- AssociatedApplicationGroupUids (System.Int32[])
       List of associated application group uids.
    
    -- AssociatedApplicationGroupUUIDs (System.Guid[])
       List of associated application group UUIDs.
    
    -- AssociatedDesktopGroupPriorities (System.Int32[])
       List of directly associated desktop group priorities. Associated desktop groups is the list of desktop groups on which the application is published. When launching an application an available machine from one of the associated groups is selected. Desktop groups are searched for available machines in order of their priority.
    
    -- AssociatedDesktopGroupUids (System.Int32[])
       List of directly associated desktop group uids. Associated desktop groups is the list of desktop groups on which the application is published. The list is sorted by priority, with the highest priority group first.
    
    -- AssociatedDesktopGroupUUIDs (System.Guid[])
       List of directly associated desktop group UUIDs. Associated desktop groups is the list of desktop groups on which the application is published. The list is sorted by priority, with the highest priority group first.
    
    -- AssociatedUserFullNames (System.String[])
       List of associated users (full names). Associated users is the list of users who are given access using the application/user mapping filter.
    
    -- AssociatedUserNames (System.String[])
       List of associated users (SAM names). Associated users is the list of users who are given access using the application/user mapping filter.
    
    -- AssociatedUserUPNs (System.String[])
       List of associated users (user principle names). Associated users is the list of users who are given access using the application/user mapping filter.
    
    -- BrowserName (System.String)
       Unique browser name used to identify this application to other components in the site. This value is not visible to the end users.
    
    -- ClientFolder (System.String)
       The folder that the application belongs to as the user sees it.
    
    -- CommandLineArguments (System.String)
       The command-line arguments to use when launching the executable.
    
    -- CommandLineExecutable (System.String)
       The name including the full path of the executable file to launch.
    
    -- ConfigurationSlotUids (System.Int32[])
       Uids of any configuration slots which hold machine configurations associated with the application. The order of slot UIDs in this list correspond with the order of items in the associated MachineConfigurationNames and MachineConfigurationUids list properties, and so the same slot UID can appear more than once.
    
    -- CpuPriorityLevel (Citrix.Broker.Admin.SDK.CpuPriorityLevel)
       The CPU priority of the launched process. Valid values are: Low, BelowNormal, Normal, AboveNormal, and High.
    
    -- Description (System.String)
       Optional application description. This description is visible to the end users.
    
    -- Enabled (System.Boolean)
       Specifies whether or not this application can be launched.
    
    -- HomeZoneName (System.String)
       Name of optional preferred home zone for launching the application.
    
    -- HomeZoneOnly (System.Boolean)
       Indicates that if the preferred zone for launching the application is its home zone but no machine is available from that zone then the launch fails.
    
    -- HomeZoneUid (System.Guid?)
       Optional preferred home zone for launching the application.
    
    -- IconFromClient (System.Boolean)
       Specifies if the app icon should be retrieved from the application on the client. This is reserved for possible future use, and all applications of type HostedOnDesktop cannot set or change this value.
    
    -- IconUid (System.Int32?)
       The icon UID used for this application. If not specified a generic icon is used.
    
    -- IgnoreUserHomeZone (System.Boolean)
       Indicates that when launching the application and the user has a home zone specified then the user's home zone preference should be ignored.
    
    -- MachineConfigurationNames (System.String[])
       The MachineConfiguration names associated with the application.
    
    -- MachineConfigurationUids (System.Int32[])
       The MachineConfiguration uids associated with the application.
    
    -- MaxPerUserInstances (System.Int32)
       Maximum allowed concurrently running instances of the application that an individual user can have. A value of zero allows unlimited usage subject to any site-wide limit.
    
    -- MaxTotalInstances (System.Int32)
       Maximum allowed total of concurrently running instances of the application in the site. A value of zero allows unlimited usage.
    
    -- MetadataKeys (System.String[])
       All key names of metadata items associated with this application.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this application.
    
    -- Name (System.String)
       Unique administrative name of application; this will include any parent admin folder hierarchy separated by backslash characters.
    
    -- PublishedName (System.String)
       Published name of application as seen by end user. If not specified value used defaults to the administrative name.
    
    -- SecureCmdLineArgumentsEnabled (System.Boolean)
       Specifies whether the command-line arguments should be secured.
    
    -- ShortcutAddedToDesktop (System.Boolean)
       Specifies whether a shortcut to the application should be placed on the user device.
    
    -- ShortcutAddedToStartMenu (System.Boolean)
       Specifies whether a shortcut to the application should be placed in the user's Start menu on their user device.
    
    -- StartMenuFolder (System.String)
       The name of the Start menu folder that holds the application shortcut.
    
    -- Tags (System.String[])
       A list of tags associated with the application.
    
    -- Uid (System.Int32)
       A unique identifier of the application.
    
    -- UserFilterEnabled (System.Boolean)
       Indicates if application-specific user filter is enabled.
    
    -- UUID (System.Guid)
       UUID of the application.
    
    -- Visible (System.Boolean)
       Specifies if the application is visible to users.
    
    -- WaitForPrinterCreation (System.Boolean)
       Specifies whether the VDA delays starting the app until printers are set up or not.
    
    -- WorkingDirectory (System.String)
       The working directory the executable is launched from.
    

## 相关命令

- [New-BrokerApplication](New-BrokerApplication.html)
- [Add-BrokerApplication](Add-BrokerApplication.html)
- [Remove-BrokerApplication](Remove-BrokerApplication.html)
- [Rename-BrokerApplication](Rename-BrokerApplication.html)
- [Move-BrokerApplication](Move-BrokerApplication.html)
- [Set-BrokerApplication](Set-BrokerApplication.html)

## 参数

| 名称                             | 说明                                                                                                                                                                                                                                                                                                                             | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                            | Gets only the application with the specified unique identifier.                                                                                                                                                                                                                                                                | true  | false |                                                                                        |
| 名称                             | Gets only the applications matching the specified name (including any parent admin folder hierarchy.                                                                                                                                                                                                                           | false | false |                                                                                        |
| AdminFolderName                | Gets applications that are in admin folders matching the specified name.                                                                                                                                                                                                                                                       | false | false |                                                                                        |
| AdminFolderUid                 | Gets applications that are in the specified admin folder.                                                                                                                                                                                                                                                                      | false | false |                                                                                        |
| AllAssociatedDesktopGroupUid   | Gets applications associated with the desktop group identified by the uid.  
The application may be either published directly on the desktop group or published indirectly on the desktop group as part of an application group.                                                                                               | false | false |                                                                                        |
| AllAssociatedDesktopGroupUUID  | Gets applications associated with the desktop group identified by the UUID.  
The application may be either published directly on the desktop group or published indirectly on the desktop group as part of an application group.                                                                                              | false | false |                                                                                        |
| ApplicationName                | Gets applications that match the specified simple name.                                                                                                                                                                                                                                                                        | false | false |                                                                                        |
| ApplicationType                | Gets applications that match the type specified: HostedOnDesktop, InstalledOnClient or PublishedContent.                                                                                                                                                                                                                       | false | false |                                                                                        |
| AssociatedApplicationGroupUid  | Gets applications that are members of the application group identified by the uid.                                                                                                                                                                                                                                             | false | false |                                                                                        |
| AssociatedApplicationGroupUUID | Gets applications that are members of the application group identified by the UUID.                                                                                                                                                                                                                                            | false | false |                                                                                        |
| AssociatedDesktopGroupPriority | Gets applications with an associated desktop group identified by priority assigned to the pairing between an application and desktop group.  
Associated desktop group is a desktop group on which the application is published.                                                                                               | false | false |                                                                                        |
| AssociatedDesktopGroupUid      | Gets applications directly associated with the desktop group identified by the uid.  
The application must be published directly on the desktop group. To search for applications that may be published indirectly on the desktop group as part of an application group, use the AllAssociatedDesktopGroupUid filter instead.  | false | false |                                                                                        |
| AssociatedDesktopGroupUUID     | Gets applications directly associated with the desktop group identified by the UUID.  
The application must be published directly on the desktop group. To search for applications that may be published indirectly on the desktop group as part of an application group, use the AllAssociatedDesktopGroupUid filter instead. | false | false |                                                                                        |
| AssociatedUserFullName         | Gets applications with an associated user identified by their full name (usually 'first-name last-name').  
If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules).                         | false | false |                                                                                        |
| AssociatedUserName             | Gets applications with an associated user identified by their user name (in the form 'domain\user'). If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules).                               | false | false |                                                                                        |
| AssociatedUserUPN              | Gets applications with an associated user identified by their user principle name (in the form 'user@domain'). If the ‘UserFilterEnabled’ property is true then access to the application is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules).                      | false | false |                                                                                        |
| BrowserName                    | Gets only the applications that match the supplied name. The BrowserName is usually an internal name for the application and is unique in the site.                                                                                                                                                                            | false | false |                                                                                        |
| ClientFolder                   | Gets only the applications that match the specified value for the folder the application belongs to as seen by the end-user. This folder can be seen in the Citrix Online Plug-in, in Web Services, and also potentially in the user's start menu.                                                                             | false | false |                                                                                        |
| CommandLineArguments           | Gets only the applications that match the supplied arguments to the command-line executable.                                                                                                                                                                                                                                   | false | false |                                                                                        |
| CommandLineExecutable          | Gets only the applications that match the supplied command-line executable.                                                                                                                                                                                                                                                    | false | false |                                                                                        |
| CpuPriorityLevel               | Gets only the applications that have the specified value for the CPU priority level of the launched executable. Valid values are: Low, BelowNormal, Normal, AboveNormal, and High.                                                                                                                                             | false | false |                                                                                        |
| 说明                             | Gets only the applications that match the supplied description.                                                                                                                                                                                                                                                                | false | false |                                                                                        |
| 已启用                            | Gets only the applications that have the specified value for whether the application is enabled. Disabled applications are still visible to users (that is controlled by the Visible setting) but cannot be launched.                                                                                                          | false | false |                                                                                        |
| HomeZoneName                   | Gets only applications with a home zone preference matching the specified name.                                                                                                                                                                                                                                                | false | false |                                                                                        |
| HomeZoneOnly                   | Gets only applications that have the specified behaviour with respect to forcing use of their home zone during launch.                                                                                                                                                                                                         | false | false |                                                                                        |
| HomeZoneUid                    | Gets only applications with a home zone preference matching the specified UID.                                                                                                                                                                                                                                                 | false | false |                                                                                        |
| IconFromClient                 | Gets only the applications that have the specified value for whether the application icon should be retrieved from the user device.                                                                                                                                                                                            | false | false |                                                                                        |
| IconUid                        | Gets only the applications that use the specified icon (identified by its Uid).                                                                                                                                                                                                                                                | false | false |                                                                                        |
| IgnoreUserHomeZone             | Gets only applications that have the specified behaviour with respect to ignoring user home zones during launch.                                                                                                                                                                                                               | false | false |                                                                                        |
| MaxPerUserInstances            | Gets only applications with the specified maximum allowed concurrently running instances that an individual user can have.                                                                                                                                                                                                     | false | false |                                                                                        |
| MaxTotalInstances              | Gets only applications with the specified maximum allowed total of concurrently running instances in the site.                                                                                                                                                                                                                 | false | false |                                                                                        |
| MetadataKey                    | Gets only applications whose associated metadata contains key names matching the specified value.                                                                                                                                                                                                                              | false | false |                                                                                        |
| 元数据                            | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                                                                                                                                      | false | false |                                                                                        |
| PublishedName                  | Gets applications whose published name matches the supplied pattern.                                                                                                                                                                                                                                                           | false | false |                                                                                        |
| SecureCmdLineArgumentsEnabled  | Gets only the applications that have the specified value for whether the command-line arguments should be secured. This is reserved for possible future use, and all applications of type HostedOnDesktop can only have this value set to true.                                                                                | false | false |                                                                                        |
| ShortcutAddedToDesktop         | Gets only the applications that match depending on whether a shortcut for the application has been added to the user device or not.                                                                                                                                                                                            | false | false |                                                                                        |
| ShortcutAddedToStartMenu       | Gets only the applications that match depending on whether a shortcut for the application has been added to Start Menu of the user device or not.                                                                                                                                                                              | false | false |                                                                                        |
| StartMenuFolder                | Gets only the applications that match the specified name for the start menu folder that holds the application shortcut. This is valid only for the Citrix Online Plug-in.                                                                                                                                                      | false | false |                                                                                        |
| 标记                             | Gets applications associated with the specified tag.                                                                                                                                                                                                                                                                           | false | false |                                                                                        |
| UserFilterEnabled              | Gets only applications whose user filter is in the specified state.                                                                                                                                                                                                                                                            | false | false |                                                                                        |
| UUID                           | Gets applications with the specified value of UUID.                                                                                                                                                                                                                                                                            | false | false |                                                                                        |
| Visible                        | Gets only the applications that have the specified value for whether it is visible to the users.                                                                                                                                                                                                                               | false | false |                                                                                        |
| WaitForPrinterCreation         | Gets only the applications that match depending on whether the VDA delays starting the application until printers are set up.                                                                                                                                                                                                  | false | false |                                                                                        |
| WorkingDirectory               | Gets only the applications that match the specified working directory.                                                                                                                                                                                                                                                         | false | false |                                                                                        |
| DesktopUid                     | Gets only the applications that have been associated (using a desktop group) to the specified desktop (identified by its Uid). Note that an application is not directly associated with a desktop, but only indirectly by which desktop group it has been published to.                                                        | false | false |                                                                                        |
| ApplicationGroupUid            | Gets applications that are members of the application group identified by the uid.                                                                                                                                                                                                                                             | false | false |                                                                                        |
| SessionUid                     | Gets only the applications that are running in the specified session (identified by its Uid).                                                                                                                                                                                                                                  | false | false |                                                                                        |
| UserSID                        | Gets only applications with their accessibility restricted to include the specified user.                                                                                                                                                                                                                                      | false | false |                                                                                        |
| DesktopGroupUid                | Gets only the applications that have been published to the specified desktop group (identified by its Uid).                                                                                                                                                                                                                    | false | false |                                                                                        |
| MachineConfigurationUid        | Gets only applications which have an associated machine configuration identified by the given Uid.                                                                                                                                                                                                                             | false | false |                                                                                        |
| ReturnTotalRecordCount         | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                                                                                                                               | false | false | False                                                                                  |
| MaxRecordCount                 | 指定要返回的最大记录数。                                                                                                                                                                                                                                                                                                                   | false | false | 250                                                                                    |
| 跳过                             | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                                                                                                                          | false | false |                                                                                        |
| SortBy                         | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                                                                                                                       | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                            | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                                                                                                                        | false | false |                                                                                        |
| 属性                             | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                                                                                                                         | false | false |                                                                                        |
| AdminAddress                   | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                             | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.Application

Get-BrokerApplication returns an object for each application it gets.## Notes Get-BrokerApplication returns just the application object, and as such is not a complete picture. The returned objects do not tell you what File-Type Associations are configured for this application, etc.  
Use the following cmdlets to gather data related to applications (shown with examples of syntax):  
Get-BrokerConfiguredFTA -ApplicationUid $app.Uid  
Get-BrokerTag -ApplicationUid $app.Uid  
Get-BrokerDesktopGroup -ApplicationUid $app.Uid  
Get-BrokerDesktop -PublishedApplication $app  
Get-BrokerSession -ApplicationUid $app.Uid  
Get-BrokerApplicationInstance -ApplicationUid $app.Uid

## 示例

### 示例 1

    C:\PS> Get-BrokerApplication Notepad
    

Description  
\---\---\-----  
Returns the application with the Name of "Notepad".

### 示例 2

    C:\PS> Get-BrokerApplication -PublishedName Note* -Enabled $true
    

Description  
\---\---\-----  
Returns the applications that have a PublishedName starting with "Note" and that are enabled.