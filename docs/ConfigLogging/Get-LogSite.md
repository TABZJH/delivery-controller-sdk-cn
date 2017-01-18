# Get-LogSite

Gets global configuration logging settings.

## 语法

    Get-LogSite [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet retrieves the global configuration logging settings.

## 相关命令

- [Set-LogSite](Set-LogSite.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ConfigurationLogging.Sdk.Site

Get-LogSite returns an object containing the following properties:  
o Locale - the current language that logs should be recorded in. Can be: 'en', 'ja', 'zh-CN', 'de', 'es' or 'fr'.  
o State - the current state of configuration logging. Can be: Enabled, Disabled, Mandatory or NotSupported.

## 示例

### 示例 1

    C:\PS> Get-LogSite
    

Description  
\---\---\-----  
Gets configiration logging site settings.