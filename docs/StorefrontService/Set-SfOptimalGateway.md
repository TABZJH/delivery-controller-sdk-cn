# Set-SfOptimalGateway

Set the farms and the optimal gateway to use for launch.

## 语法

    Set-SfOptimalGateway -SiteId <Int64> -ResourcesVirtualPath <String> -HostNames <String[]> -StaUrls <String[]> -Farm <String> [-StasBypassDuration <TimeSpan>] [-StasUseLoadBalancing] [-EnableSessionReliability] [-UseTwoTickets] [-EnabledOnDirectAccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Set the farms and the optimal gateway to use for launch.

## 相关命令

- [Get-SfOptimalGatewayCommand](Get-SfOptimalGatewayCommand.html)
- [Remove-SfOptimalGatewayCommand](Remove-SfOptimalGatewayCommand.html)

## 参数

| 名称                       | 说明                                                                                                                                                                                                                                                                                                                                                                   | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| SiteId                   | Site ID within IIS. This is typically 1 for the site in IIS where StoreFront is installed by default.                                                                                                                                                                                                                                                                | true  | true (ByPropertyName) |                                       |
| ResourcesVirtualPath     | Path to the store that is to be configured to have a farm to optimal gateway mapping.  
Example: “/Citrix/Store”                                                                                                                                                                                                                                                     | true  | true (ByPropertyName) |                                       |
| HostNames                | Specifies the fully qualified domain name (FQDN) and port of the optimal NetScaler Gateway appliance.  
Example1 for standard vServer port 443: gateway.example.com  
Example2 for nonstandard vServer port 500: gateway.example.com:500                                                                                                                             | true  | false                 |                                       |
| StaUrls                  | 指定运行 Secure Ticket Authority (STA) 的 XenDesktop、XenApp 和 VDI-in-a-Box 服务器的 URL。 If using multiple farms, list the STA servers on each using a comma separated list:  
Example: "http://xenapp-a.ptd.com/scripts/ctxsta.dll","http://xendesktop-a.ptd.com/scripts/ctxsta.dll"                                                                                         | true  | false                 |                                       |
| 场                        | Specificies the set of delivery controllers, as named when they were configured with StoreFront.                                                                                                                                                                                                                                                                     | true  | false                 |                                       |
| StasBypassDuration       | 设置在请求失败后将 STA 视为不可用的时间期限，采用小时、分钟和秒格式。                                                                                                                                                                                                                                                                                                                                | false | false                 |                                       |
| StasUseLoadBalancing     | Set to true: randomly obtains session tickets from all STAs, evenly distributing requests across all the STAs.  
Set to false: users are connected to the first available STA in the order in which they are listed in the configuration, minimizing the number of STAs in use at any given time.                                                                    | false | false                 |                                       |
| EnableSessionReliability | 设置为 True：在 Receiver 自动尝试重新连接时，保持断开连接的会话处于打开状态。 If you configured multiple STAs and want to ensure that session reliability is always available, set the value of the UseTwoTickets attribute to true to obtain session tickets from two different STAs in case one STA becomes unavailable during the session.                                                       | false | false                 |                                       |
| UseTwoTickets            | Set to true: obtains session tickets from two different STAs in case one STA becomes unavailable during the session.  
Set to false: uses only a single STA server.                                                                                                                                                                                                  | false | false                 |                                       |
| EnabledOnDirectAccess    | Set to true: ensures that when local users on the internal network log on to StoreFront directly, connections to their resources are still routed through the optimal appliance defined for the farm.  
Set to false: connections to resources are not routed through the optimal appliance for the farm unless users access StoreFront through a NetScaler Gateway. | false | false                 |                                       |
| LoggingId                | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                               | false | false                 |                                       |
| AdminAddress             | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                           | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

## 返回值

### 无

## 示例

### 示例 1

    C:\PS>Set-DSOptimalGatewayForFarms -SiteId 1 -ResourcesVirtualPath /Citrix/Store -Hostnames @("gateway1.citrix.com:2222") -StaUrls @("https://server1.citrix.com/staurl") -StasBypassDuration "00.02:00:00" -EnabledOnDirectAccess
    

说明  
\---\---\-----