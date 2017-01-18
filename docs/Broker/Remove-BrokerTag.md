# Remove-BrokerTag

Removes tag to object associations or deletes tags from the site altogether.

## 语法

    Remove-BrokerTag [-Tags] <Tag[]> [-AllApplications] [-AllApplicationGroups] [-AllDesktops] [-AllDesktopGroups] [-AllMachines] [-AllObjects] [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerTag [-InputObject] <Tag[]> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-BrokerTag [-Name] <String> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes the association between tags and objects within the site, or deletes tags from the site altogether.

To remove an association, supply one of the Application, Machine, Desktop or DesktopGroup parameters.

To delete a tag entirely, together with any associations between the tag and other objects in the site, specify the tag without any associated object parameter.

## 相关命令

- [Add-BrokerTag](Add-BrokerTag.html)
- [Get-BrokerTag](Get-BrokerTag.html)
- [New-BrokerTag](New-BrokerTag.html)
- [Rename-BrokerTag](Rename-BrokerTag.html)
- [Set-BrokerTag](Set-BrokerTag.html)

## 参数

| 名称                   | 说明                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| 标记                   | Specifies one or more tag objects.                                                                                                                                              | true  | true (ByValue)        |                                                                                        |
| InputObject          | Specifies one or more tag objects.                                                                                                                                              | true  | true (ByValue)        |                                                                                        |
| 名称                   | Specifies a tag by name.                                                                                                                                                        | true  | true (ByPropertyName) |                                                                                        |
| AllApplications      | Remove the specified tags from all applications.                                                                                                                                | false | false                 |                                                                                        |
| AllApplicationGroups | Remove the specified tags from all application groups.                                                                                                                          | false | false                 |                                                                                        |
| AllDesktops          | Remove the specified tags from all desktops.                                                                                                                                    | false | false                 |                                                                                        |
| AllDesktopGroups     | Remove the specified tags from all desktop groups.                                                                                                                              | false | false                 |                                                                                        |
| AllMachines          | Remove the specified tags from all machines.                                                                                                                                    | false | false                 |                                                                                        |
| AllObjects           | Remove the specified tags from all objects.                                                                                                                                     | false | false                 |                                                                                        |
| 应用程序                 | Removes the association between the given tag and application.                                                                                                                  | false | true (ByValue)        |                                                                                        |
| ApplicationGroup     | Removes the association between the given tag and application group.                                                                                                            | false | true (ByValue)        |                                                                                        |
| 桌面                   | Removes the association between the given tag and desktop.                                                                                                                      | false | true (ByValue)        |                                                                                        |
| DesktopGroup         | Removes the association between the given tag and desktop group.                                                                                                                | false | true (ByValue)        |                                                                                        |
| 计算机                  | Removes the association between the given tag and machine.                                                                                                                      | false | true (ByValue)        |                                                                                        |
| LoggingId            | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                                                                        |
| AdminAddress         | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Tag

Tags may be specified through pipeline input.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Remove-BrokerTag $tag -Machine $machine
    

Description  
\---\---\-----  
Removes the association between a tag and a desktop. The tag itself continues to exist in the site.

### 示例 2

    C:\PS> Remove-BrokerTag $tag
    

Description  
\---\---\-----  
Deletes the tag from the site also removing any associations that may exist between the tag and other objects.