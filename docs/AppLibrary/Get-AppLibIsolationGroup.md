# Get-AppLibIsolationGroup

Gets the details of an isolation group held in the application library.

## 语法

    Get-AppLibIsolationGroup [[-IsolationGroupUid] <Int32>] [-IncludePolicy <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The application library holds the information about isolation groups, their location on the network and the packages they contain.

## 相关命令

## 参数

| 名称                | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IsolationGroupUid | The App Library's internal unique identifier of the isolation group.                                                                                                   | false | true (ByPropertyName) |                                       |
| IncludePolicy     | The option to retrieve the Isolation Group policy.                                                                                                                     | false | true (ByPropertyName) |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.IsolationGroup

An object representing the details needed to identify an isolation group.## Notes Pass in the isolation group's uid to retreive a single isolation group.  
Pass in a library uid to retrieve all of the isolation groups in that library.  
Call the cmdlet without any parameters to retieve all of the isolation groups in the AppLibrary.

## 示例

### 示例 1

    Get-AppLibIsolationGroup
    

Description  
\---\---\-----  
Gets the details for all of the isolation groups in the AppLibrary.

### 示例 2

    Get-AppLibIsolationGroup -Name "MyIsolationGroup"
    

Description  
\---\---\-----  
Gets the details of the isolation group named MyIsolationGroup.

### 示例 3

    Get-AppLibIsolationGroup -libraryUid 1
    

Description  
\---\---\-----  
Gets the details for all of the isolation groups in the specified library.