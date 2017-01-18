# Get-ConfigEnabledFeature

Lists features of the site that are enabled.

## 语法

    Get-ConfigEnabledFeature [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

- [Set-ConfigSite](Set-ConfigSite.html)
- [Import-ConfigFeatureTable](Import-ConfigFeatureTable.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.String

## 示例

### 示例 1

    C:\PS> Get-ConfigEnabledFeature
    

Description  
\---\---\-----  
Retrieves the list of enabled features for the site's current configuration.