# New-BrokerIcon

Creates a new icon.

## 语法

    New-BrokerIcon [-EncodedIconData] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Accepts Base64 encoded .ICO format icon data, stores it in the database and returns an Icon object containing the Uid assigned to it.

New-BrokerIcon can be used with the Get-CtxIcon cmdlet from Citrix.Common.Commands, to obtain the Base64 icon. See Examples for a demonstration.

## 相关命令

- [Get-CtxIcon](Get-CtxIcon.html)
- [Get-BrokerIcon](Get-BrokerIcon.html)
- [Remove-BrokerIcon](Remove-BrokerIcon.html)

## 参数

| 名称              | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| EncodedIconData | Specifies the Base64 encoded .ICO format icon data.                                                                                                                             | true  | true (ByPropertyName) |                                                                                        |
| LoggingId       | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress    | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.Icon

Returns an Icon object.

## 示例

### 示例 1

    C:\PS> Add-PSSnapin Citrix.Common.Commands
    C:\PS> $ctxIcon = Get-CtxIcon -FileName C:\Windows\System32\notepad.exe -index 0
    C:\PS> $brokerIcon = New-BrokerIcon -EncodedIconData $ctxIcon.EncodedIconData
    C:\PS> $desktopGroup = Get-BrokerDesktopGroup -Name 'MyDesktopGroup'
    C:\PS> Set-BrokerDesktopGroup $desktopGroup -IconUid $brokerIcon.Uid
    

Description  
\---\---\-----  
Extracts the first icon resource from notepad.exe, and sets this as the icon for a desktop group.