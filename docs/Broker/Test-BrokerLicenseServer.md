# Test-BrokerLicenseServer

Tests whether or not a license server can be used by the broker.

## 语法

    Test-BrokerLicenseServer [-ComputerName] <String> [-AdminAddress <String>] [[-Port] <Int32>] [<CommonParameters>]
    

## 详细说明

Tests whether or not a given license server can be used by the broker.

## 相关命令

- [Get-BrokerSite](Get-BrokerSite.html)
- [Set-BrokerSite](Set-BrokerSite.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| ComputerName | The name of the license server to test (machine.domain).                                                                                           | true  | false | 无                                                                                      |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| 端口           | The port number to use on the server.                                                                                                              | false | false | 27000                                                                                  |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.string

Test-BrokerLicenseServer returns:  
o 'Compatible' - the server is a compatible license server that can be used.  
o 'Incompatible' - the server is an incompatible license server that can't be used.  
o 'Inaccessible' - the server cannot be accessed. The server may be down, unreachable, or non-existent.  
o 'InternalError - the server can't be used due to an internal error. A required licensing component on the server may not be installed, configured, or working correctly.

## 示例

### 示例 1

    C:\PS> Test-BrokerLicenseServer -LicenseServerAddress "machine.domain" 1234
    

Description  
\---\---\-----  
Tests whether or not the license server "machine.domain" with port number 1234 can be used.

### 示例 2

    C:\PS> Test-BrokerLicenseServer -LicenseServerAddress "machine.domain"
    

Description  
\---\---\-----  
Tests whether or not the license server "machine.domain" with port number 2700 can be used.