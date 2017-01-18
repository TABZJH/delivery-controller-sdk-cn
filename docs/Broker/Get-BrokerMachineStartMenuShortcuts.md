# Get-BrokerMachineStartMenuShortcuts

Retrieves the Start Menu Shortcuts from the specified machine.

## 语法

    Get-BrokerMachineStartMenuShortcuts [-MachineName] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves the shortcuts defined for all the start menu items on a particular machine. The shortcuts obtained are from the 'All users' start menu; user-specific shortcuts are not found.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| MachineName  | Specify the name of the machine to use for shortcut retrieval. The machine can be identified by DNS name, short name, SID, or name of the form domain\machine. | true  | true (ByValue) |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### None or Citrix.Broker.Admin.SDK.StartMenuShorcut

Get-BrokerMachineStartMenuShortcuts generates an array of Citrix.Broker.Admin.SDK.StartMenuShortcut objects.

## 示例

### 示例 1

    C:\PS> $shortcuts = Get-BrokerMachineStartMenuShortcuts -MachineName 'MyDomain\MyMachine'
    

Description  
\---\---\-----  
This example retrieves all Start Menu Shortcuts from 'MyDomain\MyMachine'.