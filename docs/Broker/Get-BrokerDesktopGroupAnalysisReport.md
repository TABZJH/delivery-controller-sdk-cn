# Get-BrokerDesktopGroupAnalysisReport

Gets the detailed AppDNA compatibility report for AppDisk(s) associated with a particular Desktop Group.

## 语法

    Get-BrokerDesktopGroupAnalysisReport [-InputObject] <DesktopGroup[]> [-RetrieveReportContentsAsMHT] [-AdminAddress <String>] [[-AppDiskUid] <Guid>] [<CommonParameters>]
    

## 详细说明

Gets the detailed AppDNA compatibility report for an AppDisk associated with a particular Desktop Group.

## 相关命令

- [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup.html)
- [Set-BrokerDesktopGroup](Set-BrokerDesktopGroup.html)
- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)

## 参数

| 名称                          | 说明                                                                                                                                                 | 是否必需？ | 管道输入           | 默认值                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject                 | The desktop group(s) on which to retrieve the detailed reports                                                                                     | true  | true (ByValue) |                                                                                        |
| RetrieveReportContentsAsMHT | Retrieve the report as a MHT file                                                                                                                  | false | false          |                                                                                        |
| AdminAddress                | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| AppDiskUid                  | AppDisk unique identifier. If set, the report will be filtered down to only include this AppDisk.                                                  | false | false          |                                                                                        |

## 输入类型

### Citrix.Broker.Admin.SDK.DesktopGroup

You can pipe the desktop groups to Get-BrokerDesktopGroupAnalysisReport.

## 返回值

### Citrix.Broker.Admin.SDK.AnalysisReport

The analysis reports for the desktop groups

## 示例

### 示例 1

    Get-BrokerDesktopGroupAnalysisReport -InputObject 36
    

Description  
\---\---\-----  
Retrieves the report for the desktop group with Uid 36

### 示例 2

    $appDisk = Get-AppLibAppDisk -AppDiskName "MyAppDisk"
              Get-BrokerDesktopGroupAnalysisReport -InputObject 36 -AppDiskUid $appDisk.AppDiskUid
    

Description  
\---\---\-----  
Retrieves the report for the desktop group with Uid 36 filtered down to AppDisk "MyAppDisk"