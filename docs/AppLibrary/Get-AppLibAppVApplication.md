# Get-AppLibAppVApplication

Gets the details of an a App-V application held in the application library.

## 语法

    Get-AppLibAppVApplication [[-Uid] <Int32>] [-Name <String>] [-AppVPackageUid <Int32>] [-Description <String>] [-RetrieveIcon <Boolean>] [-RetrievePolicy <Boolean>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The application library holds the information required to find and launch an App-V application on a client VDA.

## 相关命令

## 参数

| 名称                     | 说明                                                                                            | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| UID                    | The AppLibrary's internal UID of the App-V application.                                       | false | true (ByPropertyName) |                                       |
| 名称                     | The name of the application in the the App-V package.                                         | false | true (ByPropertyName) |                                       |
| AppVPackageUid         | The AppLibrary's internal UID of the App-V package that contains the application.             | false | true (ByPropertyName) |                                       |
| 说明                     | A description of the application.                                                             | false | false                 |                                       |
| RetrieveIcon           | A switch to indicate whether to return the application's icon data.                           | false | false                 |                                       |
| RetrievePolicy         | A switch to indicate whether to return the application's policy blob                          | false | false                 |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                        | false | false                 |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 请参阅 about_AppLib_Filtering 了解详细信息。 | false | false                 | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                  | false | false                 | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                         | false | false                 |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。      | false | false                 | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | 获取与 PowerShell 样式过滤表达式匹配的记录。请参阅 about_AppLib_Filtering 了解详细信息。                              | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                    | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppVApplication

An object representing the details required to launch the App-V application.## Notes Pass in the App-V application's UID to retrieve a single application.  
Pass in a package UID to retrieve all of the applications in that package.  
Call the cmdlet without any parameters to retrieve all of the applications in the library.

## 示例

### 示例 1

    Get-AppLibAppVApplication
    

Description  
\---\---\-----  
Gets the details for all of the App-V applications in the library.

### 示例 2

    Get-AppLibAppVApplication -Name "MyApp"
    

Description  
\---\---\-----  
Gets the details of the App-V application named MyApp.

### 示例 3

    Get-AppLibAppVApplication -AppVPackageUid 15
    

Description  
\---\---\-----  
Gets the details of all of the App-V applications in the specified package.