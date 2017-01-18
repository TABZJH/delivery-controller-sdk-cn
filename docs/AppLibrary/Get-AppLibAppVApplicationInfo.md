# Get-AppLibAppVApplicationInfo

Enumerates information for a given application in a given package

## 语法

    Get-AppLibAppVApplicationInfo -PackageId <String> -ApplicationId <String> -Property <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Allows you to query application information about single admin appv package. Currently only fetching filetype associations is supported. See example

## 相关命令

## 参数

| 名称            | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| PackageId     | The package Guid                                                                                                                                                       | true  | true (ByPropertyName) |                                       |
| ApplicationId | The AppV application Id                                                                                                                                                | true  | true (ByPropertyName) |                                       |
| 属性            | The properties that you'd like to get about the application                                                                                                            | true  | true (ByPropertyName) |                                       |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress  | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Object with required information wihtin object as properties

## Notes Currently only fetching file type associations are supported.

## 示例

### 示例 1

    Get-AppLibAppVApplicationInfo -PackageId "7796B8F3-713A-446F-840D-18E5171AB21A" -ApplicationId 14 -Property @('FileTypeAssociations')
    

Description  
\---\---\-----  
Fetches all the file type associations for the given application