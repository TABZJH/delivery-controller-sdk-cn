# Import-AnalyticsDataDefinition

为 Analytics Service/客户体验改善计划导入新数据定义文件。

## 语法

    Import-AnalyticsDataDefinition -DataDefinition <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

DataDefinition 文件定义应该收集哪些数据并发送给 Citrix。只能导入 Citrix 签署的 DataDefinition 文件。如果该文件未正确签署，会发生错误。

## 相关命令

## 参数

| 名称             | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DataDefinition | 新 DataDefinition 文件的路径                                                                                                                                                 | true  | false |                                       |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress   | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    c:\PS>Import-AnalyticsDataDefinition -DataDefinition c:\SignedDataDefinition.xml
    

说明  
\---\---\-----  
导入新 DataDefinition 文件。