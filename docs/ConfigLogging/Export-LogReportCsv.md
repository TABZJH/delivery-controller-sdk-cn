# Export-LogReportCsv

Exports Configuration Logging data into a CSV file.

## 语法

    Export-LogReportCsv -OutputFile <String> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet exports the Configuration Logging data into a CSV data file. The hierarchical logging data is flattened into a single CSV ‘table’. The content of CSV file is not intended to be human-readable. It is meant to be input data for external reporting or manipulation tools (for example, a spread sheet application).

## 相关命令

- [Export-LogReportHtml](Export-LogReportHtml.html)

## 参数

| 名称             | 说明                                                             | 是否必需？ | 管道输入  | 默认值                                   |
| -------------- | -------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| OutputFile     | Specifies the path to a file where the CSV data will be saved. | true  | false |                                       |
| StartDateRange | Specifies the start time of the earliest operation to include. | false | false | DateTime.Min                          |
| EndDateRange   | Specifies the end time of the latest operation to include.     | false | false | DateTime.UtcNow                       |
| AdminAddress   | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。     | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    C:\PS> Export-LogReportCsv -OutputFile "c:\MyReports\LoggingData.csv"
    

Description  
\---\---\-----  
Export all logged operations to a csv file.

### 示例 2

    C:\PS> Export-LogReportCsv -OutputFile "c:\MyReports\LoggingData.csv" -StartDateRange "2012-12-21 09:00"
    

Description  
\---\---\-----  
Export to a CSV file logged operations started on or after a specified datetime..

### 示例 3

    C:\PS> Export-LogReportCsv -OutputFile "c:\MyReports\LoggingData.csv" -StartDateRange "2012-12-21 09:00" -EndDateRange "2012-12-311 18:00"
    

Description  
\---\---\-----  
Export to a CSV file logged operations started and completed between a date range.