# Set-AnalyticsSite

设置 Analytics Service/客户体验改善计划的站点配置。http://more.citrix.com/XD-CEIP 上提供了详细信息。

## 语法

    Set-AnalyticsSite [-Enabled <Boolean>] [-NewSite <Site>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

可使用此 cmdlet 选择加入 Citrix 体验改善计划。对于高级用户，它还可以通过使用 -NewSite 参数接受新的 Citrix.Analytics.Sdk.Site 对象。

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| Enabled      | 启用或禁用 Citrix 体验改善计划功能。                                                                                                                                                 | false | false | True                                  |
| NewSite      | 新站点对象（如果您希望提供完整站点对象）。                                                                                                                                                  | false | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    c:\PS>Set-AnalyticsSite -Enabled $true
    

说明  
\---\---\-----  
启用 Citrix 体验改善计划。要禁用，则改用 $false。