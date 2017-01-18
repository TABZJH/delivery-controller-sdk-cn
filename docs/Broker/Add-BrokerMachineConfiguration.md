# Add-BrokerMachineConfiguration

Adds a machine configuration to a desktop group.

## 语法

    Add-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerMachineConfiguration [-Name] <String> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Associates a machine configuration with a desktop group. The settings in the machine configuration are then applied to the machines in the desktop group.

## 相关命令

- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
- [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)
- [Rename-BrokerMachineConfiguration](Rename-BrokerMachineConfiguration.html)
- [Remove-BrokerMachineConfiguration](Remove-BrokerMachineConfiguration.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Machine configuration to add to the desktop group.                                                                                                                              | true  | true (ByValue)        |                                                                                        |
| 名称           | Name of a machine configuration to add to the desktop group.                                                                                                                    | true  | true (ByPropertyName) |                                                                                        |
| 应用程序         | The application to which the machine configurations are added, specified by name, Uid, or instance.                                                                             | false | true (ByValue)        |                                                                                        |
| DesktopGroup | The desktop group to which the machine configurations are added, specified by name, Uid, or instance.                                                                           | false | true (ByValue)        |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.MachineConfiguration

The machine configuration to add to the desktop group.

## 返回值

### 无

## 示例

### 示例 1

    Add-BrokerMachineConfiguration -Name UPM\Conf1 -DesktopGroup 1
    

Description  
\---\---\-----  
Adds the machine configuration named UPM\Conf1 to the desktop group with Uid 1.

### 示例 2

    $mc | Add-BrokerMachineConfiguration -DesktopGroup AdminDesktops
    

Description  
\---\---\-----  
Adds the machine configuration $mc to the desktop group named "AdminDesktops".