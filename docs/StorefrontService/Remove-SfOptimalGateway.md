# Remove-SfOptimalGateway

Removes the optimal gateway for farms configuration.

## 语法

    Remove-SfOptimalGateway -SiteId <Int64> -ResourcesVirtualPath <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes the optimal gateway for farms configuration.

## 相关命令

- [Get-SfOptimalGatewayCommand](Get-SfOptimalGatewayCommand.html)
- [Set-SfOptimalGatewayCommand](Set-SfOptimalGatewayCommand.html)

## 参数

| 名称                   | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| SiteId               | Site ID within IIS. This is typically 1 for the site in IIS where StoreFront is installed by default.                                                                  | true  | true (ByPropertyName) |                                       |
| ResourcesVirtualPath | Path to the store that is to be configured to have a farm to optimal gateway mapping.  
Example: “/Citrix/Store”                                                       | true  | true (ByPropertyName) |                                       |
| LoggingId            | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress         | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

## 返回值

### 无

## 示例

### 示例 1

    C:\PS>Remove-DSOptimalGatewayForFarms -siteId 1 -ResourcesVirtualPath "/Citrix/MyStore"
    

说明  
\---\---\-----