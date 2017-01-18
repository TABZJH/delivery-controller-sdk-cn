# Get-AppLibAppVPackage

Gets the details of an App-V package held in the application library.

## 语法

    Get-AppLibAppVPackage [[-Uid] <Int32>] [-Name <String>] [-LibraryUid <Int32>] [-Description <String>] [-RetrieveIcon <Boolean>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The application library holds the information about App-V packages, their location on the network, and the applications they contain.

## 相关命令

## 参数

| 名称                     | 说明                                                                                             | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| UID                    | The AppLibrary's internal UID of the App-V package.                                            | false | true (ByPropertyName) |                                       |
| 名称                     | The name of the App-V package.                                                                 | false | true (ByPropertyName) |                                       |
| LibraryUid             | The AppLibrary's internal UID of the specific library that holds details of the App-V package. | false | true (ByPropertyName) |                                       |
| 说明                     | A description of the App-V package and its contents.                                           | false | false                 |                                       |
| RetrieveIcon           | A switch to indicate whether to return the package's icon data.                                | false | false                 |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                         | false | false                 |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 请参阅 about_AppLib_Filtering 了解详细信息。  | false | false                 | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                   | false | false                 | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                          | false | false                 |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。       | false | false                 | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | 获取与 PowerShell 样式过滤表达式匹配的记录。请参阅 about_AppLib_Filtering 了解详细信息。                               | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                     | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppVPackage

An object representing the details needed to identify an App-V package.## Notes Pass in the App-V package's UID to retrieve a single App-V package.  
Pass in a library UID to retrieve all af the packages in that library.  
Call the cmdlet without any parameters to retrieve all of the packages in the AppLibrary.

## 示例

### 示例 1

    Get-AppLibAppVPackage
    

Description  
\---\---\-----  
Gets the details of all of the App-V packages in the AppLibrary.

### 示例 2

    Get-AppLibAppVPackage -Name "MyPackage"
    

Description  
\---\---\-----  
Gets the details of the App-V package named MyPackage.

### 示例 3

    Get-AppLibAppVPackage -libraryUid 1
    

Description  
\---\---\-----  
Gets the details of all of the App-V packages in the specified library.