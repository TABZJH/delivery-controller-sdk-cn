# Set-ConfigSite

Changes the overall settings of the site.

## 语法

    Set-ConfigSite [-SiteName <String>] [-ProductCode <String>] [-ProductEdition <String>] [-ProductVersion <String>] [-LicensingModel <String>] [-LicenseServerName <String>] [-LicenseServerPort <Int32>] [-LicenseServerUri <Uri>] [-PrimaryZone <Zone>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Set-ConfigSite cmdlet modifies properties of the site.

The site is a top-level, logical representation of the XenDesktop site, from the perspective of the configuration services running within the site.

A XenDesktop installation has only a single site instance.

Modifications to the product code, product edition, product version and licensing model properties are successful only if their values are consistent with the feature table. Use the Get-ConfigProduct, Get-ConfigProductEdition, Get-ConfigProductVersion and Get-ConfigLicensingModel cmdlets to determine consistent values.

To configure the site, first import the feature table using the Import-ConfigFeatureTable cmdlet.

## 相关命令

- [Export-ConfigFeatureTable](Export-ConfigFeatureTable.html)
- [Get-ConfigSite](Get-ConfigSite.html)
- [Get-ConfigProduct](Get-ConfigProduct.html)
- [Get-ConfigProductEdition](Get-ConfigProductEdition.html)
- [Get-ConfigProductFeature](Get-ConfigProductFeature.html)
- [Get-ConfigProductVersion](Get-ConfigProductVersion.html)
- [Get-ConfigLicensingModel](Get-ConfigLicensingModel.html)

## 参数

| 名称                | 说明                                                                                                                                                                                                                                                                                                                                   | 是否必需？ | 管道输入  | 默认值                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ----- | ------------------------------------- |
| SiteName          | Changes the name of the site.                                                                                                                                                                                                                                                                                                        | false | false |                                       |
| ProductCode       | Changes the product code.  
The Get-ConfigProduct cmdlet returns a list of supported values.                                                                                                                                                                                                                                         | false | false |                                       |
| ProductEdition    | Changes the license edition. A license matching the specified edition must be available within the site's license server.  
The Get-ConfigProductEdition returns a list of supported values.                                                                                                                                         | false | false |                                       |
| ProductVersion    | Changes the product version.  
The Get-ConfigProductVersion returns a list of supported values.                                                                                                                                                                                                                                      | false | false |                                       |
| LicensingModel    | Changes the license model. A license matching the specified model must be available within the site's license server.  
The Get-ConfigLicensingModel returns a list of supported values.                                                                                                                                             | false | false |                                       |
| LicenseServerName | Changes the machine used by the brokering services to obtain licenses for desktop and application session brokering. The specified machine must be running a Citrix license server and have suitable licenses installed.  
The license server machine can be specified by its DNS name ('machine.domain') or its numeric IP address. | false | false |                                       |
| LicenseServerPort | Changes the port number on the license server machine used by the brokering services to contact the Citrix license server.                                                                                                                                                                                                           | false | false |                                       |
| LicenseServerUri  | Changes the Uri of the web server for licensing. The hostname component of this Uri must match the Site's LicenseServerName property.                                                                                                                                                                                                | false | false |                                       |
| PrimaryZone       | Changes the primary zone for the site.  
Primary zone can be specified by Uid, Name or by passing a Zone object.                                                                                                                                                                                                                     | false | false |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                               | false | false |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                           | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 站点

## 示例

### 示例 1

    C:\PS> Set-ConfigSite -ProductEdition PLT
    

Description  
\---\---\-----  
Specifies the use of a Platinum edition license. A suitable license must be available on the site's license server.