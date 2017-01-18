# Set-BrokerPrivateDesktop

Change the settings of a private desktop.

## 语法

    Set-BrokerPrivateDesktop [-InputObject] <PrivateDesktop[]> [-PassThru] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-ColorDepth <ColorDepth>] [-Description <String>] [-IconUid <Int32>] [-InMaintenanceMode <Boolean>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-BrokerPrivateDesktop [-MachineName] <String> [-PassThru] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-ColorDepth <ColorDepth>] [-Description <String>] [-IconUid <Int32>] [-InMaintenanceMode <Boolean>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Private desktops are automatically created when a machine is added to a desktop group with a DesktopKind of 'Private', and these inherit default properties. Use Set-BrokerPrivateDesktop to change the configuration settings of an existing private desktop.

To specify private desktops, you can choose whether to update by machine name, or by passing a PrivateDesktop or an array of PrivateDesktop objects. You can also use the Uid or an array of Uids instead.

You cannot modify many properties of a private desktop as these contain status information; for example DNSName, RegistrationState, and OSVersion.

Use Add- and Remove- cmdlets to update relationships between private desktops and other objects. For example, you can add a tag to a private desktop with: Add-BrokerTag $tag -Desktop $desktop.Uid

Similarly, assign users to private desktops with: Add-BrokerUser $user -PrivateDesktop $desktop

Many of the fields that can be set with this cmdlet can also be set with Set-BrokerMachine, such as MaintenanceMode. Using Set-BrokerMachine is preferred in these cases.

For more information about desktops, see about_Broker_Desktops; for more information about machines, see about_Broker_Machines.

## 相关命令

- [Get-BrokerMachine](Get-BrokerMachine.html)

## 参数

| 名称                 | 说明                                                                                                                                                                                                                                                                                       | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject        | Specifies the desktop or array of desktops to modify. You can also use an integer Uid of the desktop instead.                                                                                                                                                                            | true  | true (ByValue)        |                                                                                        |
| MachineName        | Specifies the desktop to modify using its machine name (in the form 'domain\machine').                                                                                                                                                                                                  | true  | true (ByPropertyName) |                                                                                        |
| PassThru           | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record.                                                                                                                                                           | false | false                 | False                                                                                  |
| AssignedClientName | Changes the client name assignment of the desktop. Set this to $null to remove the assignment. Desktops can be assigned to multiple users, a single IP address, or a single client name, but only to one of these categories at one time.                                                | false | false                 |                                                                                        |
| AssignedIPAddress  | Changes the IP address assignment of the desktop. Set this to $null to remove the assignment. Desktops can be assigned to multiple users, a single IP address, or a single client name, but only to one of these categories at one time.                                                 | false | false                 |                                                                                        |
| ColorDepth         | Changes the color depth connections to this desktop should use.  
Valid values are $null, FourBit, EightBit, SixteenBit, and TwentyFourBit. A value of $null results in the desktop group value being used instead.                                                                      | false | false                 |                                                                                        |
| 说明                 | Changes the description of the desktop. This is seen only by Citrix Administrators and is not visible to users.                                                                                                                                                                          | false | false                 |                                                                                        |
| IconUid            | Changes the icon displayed for this desktop. When this setting is $null, the icon displayed is determined by the desktop group.                                                                                                                                                          | false | false                 |                                                                                        |
| 处于维护模式             | Changes the maintenance mode setting of a desktop. When a desktop is in maintenance mode, it is not included as a candidate when brokering new sessions, and it does not participate in automatic power management (idle pool); however, it still responds to explicit power operations. | false | false                 |                                                                                        |
| PublishedName      | Changes the name displayed to the user for this desktop. When this setting is $null, the name displayed is determined by the PublishedName of the desktop group.                                                                                                                         | false | false                 |                                                                                        |
| SecureIcaRequired  | Changes whether or not SecureICA is required for connections to this desktop. When this setting is $null, the SecureIcaRequired setting from the desktop group is used.                                                                                                                  | false | false                 |                                                                                        |
| LoggingId          | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                          | false | false                 |                                                                                        |
| AdminAddress       | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                       | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.PrivateDesktop

You can pipe PrivateDesktop objects into this cmdlet instead of on the command line with the -InputObject parameter.

## 返回值

### None or Citrix.Broker.Admin.SDK.PrivateDesktop

This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.PrivateDesktop object.

## 示例

### 示例 1

    C:\PS> Set-BrokerPrivateDesktop DOMAIN\Machine1 -ColorDepth SixteenBit
    

Description  
\---\---\-----  
Change the color depth of Machine1 to be 16-bit.

### 示例 2

    C:\PS> Get-BrokerPrivateDesktop -InMaintenanceMode $true | Set-BrokerPrivateDesktop -InMaintenanceMode $false
    

Description  
\---\---\-----  
Bring all private desktops currently in maintenance mode back into normal service.