# Start-BrokerCatalogAnalysis

Performs a AppDNA analysis on catalog

## 语法

    Start-BrokerCatalogAnalysis [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Extracts OS metadata from a machine in the catalog and uploads it to AppDNA server

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Specifies the catalog to perform the analysis on.                                                                                                                               | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

You can pipe in the catalogs on which to start the catalog analysis on.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Set-BrokerCatalogAnalysis -InputObject $obj-Uid
    

Description  
\---\---\-----  
This command starts a catalog analysis for the Catalog whose instance is pointed by $obj-Uid