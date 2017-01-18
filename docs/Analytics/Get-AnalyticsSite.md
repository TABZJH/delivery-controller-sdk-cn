# Get-AnalyticsSite

此 cmdlet 返回 Analytics Service/客户体验改善计划的站点配置。http://more.citrix.com/XD-CEIP 上提供了详细信息。

## 语法

    Get-AnalyticsSite [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

配置将包含在返回的站点对象中。 站点对象具有 Enabled 和 DataDefinitionVersion 两个属性。 如果 Enabled 为 True，则站点正在参与 Citrix 体验改善计划。

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Analytics.Sdk.Site

具有配置属性的站点对象。

## 示例

### 示例 1

    c:\PS>Get-AnalyticsSite
    
              DataDefinitionVersion                           Enabled
              ---------------------                           -------
              1.0.0                                           False
    

说明  
\---\---\-----  
检索 Analytics 站点配置。