# Export-LogReportHtml

Exports Configuration Logging data into a HTML report.

## 语法

    Export-LogReportHtml -OutputDirectory <String> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This cmdlet exports the Configuration Logging data into a HTML report. The report consists of two HTML files: o Summary.Html - this shows summary information from the high level operation logs. o Details.Html - this shows additional logging data from the low level operation and operation detail logs. Hyperlinks in summary.html allow drill-down into the associated low level logging data contained within details.html.

## 相关命令

- [Export-LogReportCsv](Export-LogReportCsv.html)

## 参数

| 名称              | 说明                                                                                | 是否必需？ | 管道输入  | 默认值                                   |
| --------------- | --------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| OutputDirectory | Specifies the path to a directory where the HTML report files will will be saved. | true  | false |                                       |
| StartDateRange  | Specifies the start time of the earliest operation to include.                    | false | false | DateTime.Min                          |
| EndDateRange    | Specifies the end time of the latest operation to include.                        | false | false | DateTime.UtcNow                       |
| AdminAddress    | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                        | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports"
    

Description  
\---\---\-----  
Export all logged operations to HTML.

### 示例 2

    C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports" -StartDateRange "2012-12-21 09:00"
    

Description  
\---\---\-----  
Export to a HTML logged operations started on or after a specified datetime..

### 示例 3

    C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports" -StartDateRange "2012-12-21 09:00" -EndDateRange "2012-12-311 18:00"
    

Description  
\---\---\-----  
Export to HTML logged operations started and completed between a date range.