# Get-HypVolumeServiceConfiguration

Gets instances of the VolumeServiceConfiguration that are configured for this site.

## 语法

    Get-HypVolumeServiceConfiguration [[-VolumeServiceConfigurationName] <String>] [-VolumeServiceConfigurationUid <Guid>] [-ConnectionType <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieve VolumeServiceConfigurations whose properties match the given filter criteria. If no parameters are specified, this cmdlet retrieves all VolumeServiceConfiguration objects.

## 相关命令

- [Set-HypVolumeServiceConfiguration](Set-HypVolumeServiceConfiguration.html)

## 参数

| 名称                             | 说明                                                                                                   | 是否必需？ | 管道输入                           | 默认值                                   |
| ------------------------------ | ---------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| VolumeServiceConfigurationName | Specifies a filter for the configuration name.                                                       | false | true (ByValue, ByPropertyName) |                                       |
| VolumeServiceConfigurationUid  | Specifies a filter for the configuration ID.                                                         | false | true (ByPropertyName)          |                                       |
| ConnectionType                 | Specifies a filter for the cloud connection type, such as "AWS" or "CloudPlatform".                  | false | false                          |                                       |
| 属性                             | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                               | false | false                          |                                       |
| ReturnTotalRecordCount         | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Hyp_Filtering for details.      | false | false                          | False                                 |
| MaxRecordCount                 | 指定要返回的最大记录数。                                                                                         | false | false                          | 250                                   |
| 跳过                             | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                | false | false                          |                                       |
| SortBy                         | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。             | false | false                          | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                            | Gets records that match a PowerShell-style filter expression. See about_Hyp_Filtering for details. | false | false                          |                                       |
| AdminAddress                   | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                           | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 字符串

The name of a configuration (or set of configurations) to retrieve.

## 返回值

### Citrix.Host.Sdk.VolumeServiceConfiguration

This cmdlet returns matching VolumeServiceConfiguration objects.

## 示例

### 示例 1

    C:\PS>Get-HypVolumeServiceConfiguration -VolumeServiceConfigurationName SiteDefault -ConnectionType CloudPlatform
    

Description  
\---\---\-----  
This command lists the site default volume service configuration for connections that use Citrix Cloud Platform.