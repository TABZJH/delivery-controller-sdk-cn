# Start-BrokerNaturalDesktopGroupRebootCycle

Reboots all machines from the specified desktop group when they are not in use.

## 语法

    Start-BrokerNaturalDesktopGroupRebootCycle [-InputObject] <DesktopGroup[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creating a natural reboot cycle for a desktop group ensures that all machines in the group are running the most recent image for the group.

The machines are rebooted in a non-disruptive manner, allowing machines that are in use to continue working and be restarted only after they become idle.

## 相关命令

- [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)
- [Start-BrokerDesktopGroupRebootCycle](Start-BrokerDesktopGroupRebootCycle.html)
- [Start-BrokerNaturalRebootCycle](Start-BrokerNaturalRebootCycle.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Reboots all machines from this input desktop group. The desktop groups can be specified using UID values, name values (including wildcards) or desktop group objects.           | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.DesktopGroup

Desktop Groups may be specified through pipeline input. The desktop groups can be specified using UID values, name values (including wildcards) or desktop groups objects

## 返回值

### 无

## Notes Natural reboot cycles do not apply to non-power managed machines or multi-session desktop groups

## 示例

### 示例 1

    $dg = Get-BrokerDesktopGroup -Uid 1
              Start-BrokerNaturalDesktopGroupRebootCycle -InputObject $dg
    

Description  
\---\---\-----  
The above code applies a natural reboot cycle on desktop group with Id 1