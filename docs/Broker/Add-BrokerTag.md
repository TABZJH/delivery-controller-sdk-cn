# Add-BrokerTag

Associate a tag with another object in the site.

## 语法

    Add-BrokerTag [-InputObject] <Tag[]> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-BrokerTag [-Name] <String> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Associates one or more tags with a machine, application group, application, desktop group or desktop within the site.

## 相关命令

- [Get-BrokerTag](Get-BrokerTag.html)
- [New-BrokerTag](New-BrokerTag.html)
- [Remove-BrokerTag](Remove-BrokerTag.html)
- [Rename-BrokerTag](Rename-BrokerTag.html)
- [Set-BrokerTag](Set-BrokerTag.html)

## 参数

| 名称               | 说明                                                                                                                                                                                  | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| InputObject      | Specifies one or more tag objects.                                                                                                                                                  | true  | true (ByValue)        |                                                                                        |
| 名称               | Specifies a tag by name.                                                                                                                                                            | true  | true (ByPropertyName) |                                                                                        |
| 应用程序             | Associates the tag with the specified application.                                                                                                                                  | false | true (ByValue)        |                                                                                        |
| ApplicationGroup | Associates the tag with the specified application group.                                                                                                                            | false | true (ByValue)        |                                                                                        |
| 桌面               | Associates the tag with the specified desktop. The tag is associated with the underlying machine not with the desktop itself.  
This parameter is deprecated, use -Machine instead. | false | true (ByValue)        |                                                                                        |
| DesktopGroup     | Associates the tag with the specified desktop group.                                                                                                                                | false | true (ByValue)        |                                                                                        |
| 计算机              | Associates the tag with the specified machine.                                                                                                                                      | false | true (ByValue)        |                                                                                        |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。     | false | false                 |                                                                                        |
| AdminAddress     | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                  | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Tag

Tags may be specified through pipeline input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Add-BrokerTag -Name 'Tag1' -Machine DOMAIN\Machine
    

Description  
\---\---\-----  
Associates 'Tag1' with machine DOMAIN\Machine.

### 示例 2

    C:\PS> $machine = Get-BrokerMachine -Uid 1
    C:\PS> New-BrokerTag 'Tag2' | Add-BrokerTag -Machine $machine
    

Description  
\---\---\-----  
Creates a new tag with name 'Tag2' and associates it with the machine with Uid 1.