# Get-AppLibAppDiskAppDNAReport

获取 AppDisk 的 AppDNA 兼容性报告。

## 语法

    Get-AppLibAppDiskAppDNAReport [-AppDiskUid] <Guid> -FileName <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

获取指定 AppDisk 的详细 AppDNA 兼容性报告。

## 相关命令

- [Get-AppLibDesktopGroupAppDNAReport](Get-AppLibDesktopGroupAppDNAReport.html)
- [Get-AppLibDesktopGroupAppDiskAppDNAReport](Get-AppLibDesktopGroupAppDiskAppDNAReport.html)
- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AppDiskUid   | 要为其检索报告的 AppDisk 的唯一标识符。                                                                                                                                               | true  | false |                                       |
| FileName     | 报告将保存到的文件名称。                                                                                                                                                           | true  | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 字符串

## 返回值

### Citrix.AppLibrary.Sdk.AppLibraryStatus

指示报告导出操作成功的对象

## 示例

### 示例 1

    C:\PS>Get-AppLibAppDiskAppDNAReport -AppDiskUid "F0A272E2-0268-48E3-8855-CFED44236B8E" -FileName "C:\Windows\Temp\Report.mht"
    

说明  
\---\---\-----  
将指定 AppDisk 的报告保存到 C:\Windows\Temp\Report.mht

### 示例 2

    C:\PS>$AppDisk = Get-AppLibAppDisk -Name "MyAppDisk"
                C:\PS>Get-AppLibAppDiskAppDNAReport -AppDiskUid $AppDisk.ApppDiskUid -FileName "C:\Windows\Temp\Report.mht"
                C:\PS>Invoke-Item "C:\Windows\Temp\Report.mht"
    

说明  
\---\---\-----  
查找名为“My AppDisk”的 AppDisk 的 Uid，并使用它将报告保存到 C:\Windows\Temp\Report.mht