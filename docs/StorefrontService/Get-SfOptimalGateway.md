# Get-SfOptimalGateway

Gets the configured optimal gateways for farms.

## 语法

    Get-SfOptimalGateway -SiteId <Int64> -ResourcesVirtualPath <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets the configured optimal gateways for farms.

## 相关命令

- [Set-SfOptimalGatewayCommand](Set-SfOptimalGatewayCommand.html)
- [Remove-SfOptimalGatewayCommand](Remove-SfOptimalGatewayCommand.html)

## 参数

| 名称                   | 说明                                                                                                               | 是否必需？ | 管道输入                  | 默认值                                   |
| -------------------- | ---------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| SiteId               | Site ID within IIS. This is typically 1 for the site in IIS where StoreFront is installed by default.            | true  | true (ByPropertyName) |                                       |
| ResourcesVirtualPath | Path to the store that is to be configured to have a farm to optimal gateway mapping.  
Example: “/Citrix/Store” | true  | true (ByPropertyName) |                                       |
| AdminAddress         | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                       | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

## 返回值

### Citrix.Storefront.Sdk.OptimalGateway

## 示例

### 示例 1

    C:\PS>Get-DSOptimalGatewayForFarms -siteId 1 -ResourcesVirtualPath "/Citrix/MyStore"
    

说明  
\---\---\-----