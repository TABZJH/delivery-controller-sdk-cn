# Get-BrokerMachineStartMenuShortcutIcon

Retrieves a Start Menu Shortcut icon from the specified machine.

## 语法

    Get-BrokerMachineStartMenuShortcutIcon [-MachineName] <String> [-Path] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves the icon associated with a particular shortcut on a particular machine. This icon is usually used to help create a published application to access the shortcut.

## 相关命令

- [Get-BrokerMachine](Get-BrokerMachine.html)
- [New-BrokerIcon](New-BrokerIcon.html)

## 参数

| 名称           | 说明                                                                                                                                                                                          | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| MachineName  | Specify the name of the machine to use for icon retrieval for the specified shortcut path. The machine can be identified by DNS name, short name, SID, or name of the form domain\machine. | true  | true (ByValue) |                                                                                        |
| 路径           | The location of the shortcut in the specified machine whose icon is being fetched.                                                                                                          | true  | true (ByValue) |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                          | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

Get-BrokerMachineStartMenuShortcutIcon generates a Base64 encoded string containing the icon for the specified shortcut. This can be used as input to New-BrokerIcon cmdlet.

## 示例

### 示例 1

    C:\PS> $shortcuts =  Get-BrokerMachineStartMenuShortcuts -MachineName 'MyDomain\MyMachine'
    C:\PS> $encodedIconData =  Get-BrokerMachineStartMenuShortcutIcon -MachineName 'MyDomain\MyMachine' -Path $shortcuts[0].ShortcutPath
    C:\PS> $brokerIcon = New-BrokerIcon -EncodedIconData $encodedIconData
    C:\PS> Set-BrokerApplication 'Notepad' -IconUid $brokerIcon.Uid
    

Description  
\---\---\-----  
This example retrieves all Start Menu Shortcuts from 'MyDomain\MyMachine', and then the icon for the first shortcut from the returned list. The icon is then associated with a published application called 'Notepad'.