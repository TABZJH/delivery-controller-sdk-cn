# New-AppLibAppVPackage

Adds a new package to the library.

## 语法

    New-AppLibAppVPackage [-LibraryUid <Int32>] [-Path <String>] [-RetrieveIcon <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The package and the applications that make it up are added to the library.

## 相关命令

- [Remove-AppLibAppVPackage](Remove-AppLibAppVPackage.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| LibraryUid   | The UID of the library to which the package is added.                                                                                                                  | false | true (ByPropertyName) |                                       |
| 路径           | The full path to the package on the network share.                                                                                                                     | false | true (ByPropertyName) |                                       |
| RetrieveIcon | A switch to indicate whether to return the package and applications' icon data.                                                                                        | false | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppVPackage

An object representing the details of the the new package.## Notes When a package is added to the library and a record of that package already exists, the existing package is updated with the details of the new package. A package is considered as already existing when the following are true: 1) The PackageGuid and VersionGuid are the same as the existing package and the Path is the same or different. 2) The Path is the same as the existing package and the PackageGuid and/or VersionGuid are the same or different.

## 示例

### 示例 1

    Add-AppLibAppVPackage -LibraryUid 1 -Path "\\NetworkStorage.enterprise.com\Managed App-V Packages\Package.appv"
    

Description  
\---\---\-----  
Adds the package at the specified network location to the library.