# New-HypStorage

Creates a new storage tier definition for use in a subsequent New-Item operation.

## 语法

    New-HypStorage [-JobGroup] <Guid> -StorageType <StorageType> -StoragePath <String[]> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to create a new storage tier definition, this definition can then be associated with a subsequent New-Item operation via the JobGroup reference.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| JobGroup     | Specifies the JobGroup uid that is used to associate data from calls to this cmdlet with the subsequent New-Item operation.                                                                                                        | true  | false |                                       |
| StorageType  | The type of the new storage tier. Currently the only storage type is TemporaryStorage.                                                                                                                                             | true  | false |                                       |
| StoragePath  | Specifies the path to the storage that will be added. The path must be in one of the following formats: <drive>:\Connections\<connectionname>\MyStorage.storage or <drive>:\Connections\{<connection uid>}\MyStorage.storage | true  | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                         | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    c:\PS>$job = [Guid]::NewGuid()
    c:\PS>New-HypStorage -JobGroup $job -StorageType TemporaryStorage -StoragePath @('XDHyp:\Connections\MyConnection\Primary Storage.storage')
    

Description  
\---\---\-----  
The command creates a new job group with the unique id specified by $job which can subsequently be fed into the New-Item cmdlet. It defines a TemporaryStorage tier which will cause disks to be added to the storage path 'XDHyp:\Connections\MyConnection\Primary Storage.storage'.