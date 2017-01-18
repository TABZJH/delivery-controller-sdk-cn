# Get-BrokerIcon

Get stored icons.

## 语法

    Get-BrokerIcon -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerIcon [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerIcon -FileName <String> [-ServerName <String>] [-Index <Int32>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Reads a specific icon by Uid, or enumerates icons by passing no Uid.

\---\---\---\---\---\---\---\----- BrokerIcon Object The BrokerIcon object represents a single instance of an icon. It contains the following properties:

    -- EncodedIconData (System.String)
       The Base64 encoded .ICO format of the icon.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       Metadata for this command
    
    -- Uid (System.Int32)
       The UID of the icon itself.
    

## 相关命令

- [New-BrokerIcon](New-BrokerIcon.html)
- [Remove-BrokerIcon](Remove-BrokerIcon.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                            | 是否必需？ | 管道输入                  | 默认值                                                                                    |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | -------------------------------------------------------------------------------------- |
| UID                    | Gets only the icon specified by unique identifier.                                                                                                                                                                                                                                                                                                                                                                                            | true  | false                 |                                                                                        |
| FileName               | Specifies the name of a file from which to read the icon data. If the ServerName parameter is used, the FileName must be an absolute path.                                                                                                                                                                                                                                                                                                    | true  | true (ByPropertyName) |                                                                                        |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                                                                                                                                                                                                                                                                     | false | false                 |                                                                                        |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.                                                                                                                                                                                                                                                              | false | false                 | False                                                                                  |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                                                                                                                                                                                                                                                                  | false | false                 | 250                                                                                    |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                                                                                                                                                                                                                                         | false | false                 |                                                                                        |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                                                                                                                                                                                                                                      | false | false                 | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                    | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                                                                                                                                                                                                                                                                       | false | false                 |                                                                                        |
| 服务器名称                  | Specifies the name of the server. If the -FileName parameter refers to content or to a URL, the icon associated with the file type or URL is retrieved from the given server. Therefore, the server specified should have a file type handler installed for the given file type. If a local file path is specified, the server name refers to the server on which the file is located. If a UNC path is specified, the server name is unused. | false | true (ByPropertyName) |                                                                                        |
| 索引                     | Specifies the zero-based icon resource index. For example, to select the first icon, specify an index of 0. Alternatively, to select the third icon, specify an index of 2. If the specified index is larger than the number of icons in the source file or profiled application, an error will be returned.                                                                                                                                  | false | true (ByPropertyName) |                                                                                        |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                                                                                                                                                                                                                                        | false | false                 |                                                                                        |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                                                                            | false | false                 | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

Input cannot be piped to this cmdlet.

## 返回值

### Citrix.Broker.Admin.SDK.Icon

Returns an Icon object for each enumerated icon.### CtxIcon Returns a list of zero or more icons, each in CtxIcon format. The CtxIcon.IconData property is the icon in standard Microsoft ICO format.

## 示例

### 示例 1

    C:\PS> Get-BrokerIcon
    

Description  
\---\---\-----  
Enumerate all icons.

### 示例 2

    C:\PS> Get-BrokerIcon -Uid 1
    

Description  
\---\---\-----  
Get the icon with Uid 1.

### 示例 3

    C:\PS> Get-BrokerIcon -FileName icon1.dll
    

Description  
\---\---\-----  
Retrieves the icon data from a file named "icon1.dll" on this computer. If this DLL contains multiple icons, all of them are returned in sequence.

### 示例 4

    C:\PS> Get-BrokerIcon -FileName c:\icons\icon1.dll -ServerName Server1 -Index 0
    

Description  
\---\---\-----  
Retrieves only the first icon from the "c:\icons\icon1.dll" file on Server1.

### EXAMPLE 5

    C:\PS> Get-BrokerIcon -FileName \\Server1\Share\app1.profile app1.exe -Index 0
    

Description  
\---\---\-----  
Retrieves the icon data for an application named "app1.exe", contained in an application profile named "app1.profile" located on a file share path "\\SERVER1\Share". Returns only the first icon associated with that profiled application.