# New-AppLibAppVAppPublishedEvent

Records telemetry information

## 语法

    New-AppLibAppVAppPublishedEvent -ApplicationUid <Int32> -ApplicationName <String> -RepositoryTypeValue <Int32> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Indicates that an App-V application is published to a delivery group.

## 相关命令

## 参数

| 名称                  | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ApplicationUid      | The broker application Uid                                                                                                                                             | true  | false                 | None - This is a mandatory parameter  |
| ApplicationName     | The application name                                                                                                                                                   | true  | true (ByPropertyName) | None - This is a mandatory parameter  |
| RepositoryTypeValue | Indicates the source location of the application                                                                                                                       | true  | false                 | None - This is a mandatory parameter  |
| LoggingId           | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress        | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes Telemetry information is sent annonymously to CEIP(Customer Experiance Improvement Program) when the user has opted into the service.  
Only the information specified in the parameters are sent to CEIP  
RepositoryTypeValue(0) = Microsoft App-V Server  
RepositoryTypeValue(1) = Citrix AppLibrary

## 示例

### 示例 1

    New-AppLibAppVAppPublishedEventCommand -ApplicationName "BBC Ticker" -RepositoryTypeValue 1 -ApplicationUid 23
    

Description  
\---\---\-----  
Tracks that fact that BBC Ticker was published from a Microsoft App-V Server package repository

### 示例 2

    New-AppLibAppVAppPublishedEventCommand -ApplicationName "Notepad" -RepositoryTypeValue 2 -ApplicationUid 23
    

Description  
\---\---\-----  
Tracks that fact that BBC Ticker was published from a Citrix AppLibrary package repository