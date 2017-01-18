# Start-BrokerNaturalRebootCycle

Reboots all machines from the specified catalog when they are not in use.

## 语法

    Start-BrokerNaturalRebootCycle [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creating a natural reboot cycle for a catalog ensures that all machines in the catalog are running the most recent image for the catalog.

The machines are rebooted in a non-disruptive manner, allowing machines that are in use to continue working and be restarted only after they become idle.

## 相关命令

- [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)
- [Start-BrokerDesktopGroupRebootCycle](Start-BrokerDesktopGroupRebootCycle.html)
- [Start-BrokerNaturalDesktopGroupRebootCycle](Start-BrokerNaturalDesktopGroupRebootCycle.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Reboots all machines from this input catalog. The catalogs can be specified using UID values, name values (including wildcards) or catalog objects.                             | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

Catalogs may be specified through pipeline input. The catalogs can be specified using UID values, name values (including wildcards) or catalog objects

## 返回值

### 无

## Notes Natural reboot cycles do not apply to non-power managed and multi session catalogs

## 示例

### 示例 1

    $c = Get-BrokerCatalog -Uid 1
              Start-BrokerNaturalRebootCycle -InputObject $c
    

Description  
\---\---\-----  
The above code applies a natural reboot cycle on catalog with Id 1