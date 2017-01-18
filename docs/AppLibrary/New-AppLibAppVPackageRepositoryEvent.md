# New-AppLibAppVPackageRepositoryEvent

Records telemetry information

## 语法

    New-AppLibAppVPackageRepositoryEvent [-RepositoryType <Int32>] [-PackageCount <Int32>] [-Location <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Indicates that an App-V package repository is added to Citrix Studio.

## 相关命令

- [FIXME](FIXME.html)
- [FIXME](FIXME.html)

## 参数

| 名称             | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| RepositoryType | Indicates the source location of the application                                                                                                                       | false | false | None - This is a mandatory parameter  |
| PackageCount   | The number of packages in the repository                                                                                                                               | false | false | None - This is a mandatory parameter  |
| 位置             | The location(URL) of the App-v package repository                                                                                                                      | false | false | None - This is a mandatory parameter  |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress   | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Guid

Unique identifier for this repository source## Notes Telemetry information is sent annonymously to CEIP(Customer Experiance Improvement Program) when the user has opted into the service.  
Only the information specified in the parameters are sent to CEIP  
RepositoryTypeValue(0) = Microsoft App-V Server  
RepositoryTypeValue(1) = Citrix AppLibrary

## 示例

### 示例 1

    New-AppLibAppVPackageRepositoryEventCommand -RepositoryType 1 -PackageCount 32 -Location "http://appvserver.acme.com:9000"
    

Description  
\---\---\-----  
Records that a Microsoft App-V Server was used in Citrix Studio and that it contains 32 packages located at "http://appvserver.acme.com:9000"

### 示例 2

    New-AppLibAppVPackageRepositoryEventCommand -RepositoryType 2 -PackageCount 32 -Location "AppLibrary"
    

Description  
\---\---\-----  
Records that the internal Citrix AppLibrary was used in Citrix Studio and that it contains 32 packages.