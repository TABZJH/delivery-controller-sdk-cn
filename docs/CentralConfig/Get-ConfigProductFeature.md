# Get-ConfigProductFeature

Lists the supported features.

## 语法

    Get-ConfigProductFeature [-ProductCode] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Lists the supported features. Use the Get-ConfigEnabledFeature command to determine which features are currently enabled.

## 相关命令

- [Get-ConfigProduct](Get-ConfigProduct.html)
- [Get-ConfigSite](Get-ConfigSite.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Import-ConfigFeatureTable](Import-ConfigFeatureTable.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ProductCode  | The product code                                           | true  | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.String

The list of supported licensing models for the specified product code.## Notes The Get-ConfigProduct cmdlet lists the available product codes.  
The site object returned by Get-ConfigSite cmdlet contains the currently configured product code.

## 示例

### 示例 1

    C:\PS> Get-ConfigProductFeature -ProductCode "XDS"
    

Description  
\---\---\-----  
Retrieves the list of supported features for XenDesktop.