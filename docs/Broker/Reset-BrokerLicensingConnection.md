# Reset-BrokerLicensingConnection

Resets the broker's license server connection.

## 语法

    Reset-BrokerLicensingConnection [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Reset-BrokerLicensingConnection cmdlet resets the broker's connection to the license server.

Licensing changes resulting from new license files or alterations to the site-level licensing properties don't become effective immediately. There will typically be a delay as the changes are propagated across the site based on the scheduling of refresh logic built into the controllers and the license server.

Resetting the connection causes the list of available licenses for the connection to be updated. After adding licenses or changing the site-level licensing properties you can run Reset-BrokerLicensingConnection to ensure that the broker can access the new licenses immediately.

Each broker service instance holds its own connection to the license server. In order for the licensing changes to be applied immediately throughout the XenDesktop site this command needs to be run on every controller in the site.

## 相关命令

- [Get-BrokerSite](Get-BrokerSite.html)
- [Set-BrokerSite](Set-BrokerSite.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Reset-BrokerLicensingConnection
    

Description  
\---\---\-----  
Reset the broker's license server connection.