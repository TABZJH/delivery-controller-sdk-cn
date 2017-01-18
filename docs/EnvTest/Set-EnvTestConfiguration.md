# Set-EnvTestConfiguration

Sets the Environment Test Service's configuation options

## 语法

    Set-EnvTestConfiguration [-PerTypeDiscoveredObjectLimit <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the Environment Test Service's configuation options and broadcasts the changes to other machines in the Site.

## 相关命令

## 参数

| 名称                           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| PerTypeDiscoveredObjectLimit | Sets the maximum number of objects of a particular type to be explored when discovering objects during a test run. Default: 50                                         | false | false |                                       |
| LoggingId                    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress                 | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Integer

Must be greater than zero.

## 返回值

### System.String

## 示例

### 示例 1

    Set-EnvTestConfiguration -PerTypeDiscoveredObjectLimit 100
    

Description  
\---\---\-----  
Set the maximum to 100