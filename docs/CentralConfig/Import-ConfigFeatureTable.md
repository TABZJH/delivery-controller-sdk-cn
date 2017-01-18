# Import-ConfigFeatureTable

Sets the feature table of the site.

## 语法

    Import-ConfigFeatureTable [-Path] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Import-ConfigFeatureTable -Content <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

- [Export-ConfigFeatureTable](Export-ConfigFeatureTable.html)
- [Get-ConfigSite](Get-ConfigSite.html)
- [Set-ConfigSite](Set-ConfigSite.html)
- [Get-ConfigProduct](Get-ConfigProduct.html)
- [Get-ConfigProductEdition](Get-ConfigProductEdition.html)
- [Get-ConfigProductFeature](Get-ConfigProductFeature.html)
- [Get-ConfigProductVersion](Get-ConfigProductVersion.html)
- [Get-ConfigLicensingModel](Get-ConfigLicensingModel.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| 路径           | The path to the file containing the feature table                                                                                                                      | true  | false          |                                       |
| 内容           | Set the site's feature table.                                                                                                                                          | true  | true (ByValue) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    C:\PS> Import-ConfigFeatureTable $xml
    

Description  
\---\---\-----  
Specifies the use of a Platinum edition license. A suitable license must be available on the site's license server.