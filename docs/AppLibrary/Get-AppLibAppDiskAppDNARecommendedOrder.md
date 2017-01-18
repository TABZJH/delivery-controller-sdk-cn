# Get-AppLibAppDiskAppDNARecommendedOrder

将指定的 AppDisk Uid 排序为最大限度降低层排序冲突的新顺序。

## 语法

    Get-AppLibAppDiskAppDNARecommendedOrder [-AppDiskUid] <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

将指定的 AppDisk Uid 排序为最大限度降低层排序冲突的新顺序。

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AppDiskUid   | 打算一起运行的 AppDisk Uid 数组。                                                                                                                                                | true  | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.Guid

## 返回值

### System.Guid

## 示例

### 示例 1

    C:\PS>$Uids = @{"F92EB804-ECB1-4D45-80C0-610AB3FB7DB0", "E7CA2FA1-0DD3-417E-99E7-2BC312E8E359", "FDA1DCF4-8538-4455-9B91-D45E5C668F17"}
                C:\PS>Get-AppLibAppDiskAppDNARecommendedOrder -AppDiskUid $Uids
    
                F92EB804-ECB1-4D45-80C0-610AB3FB7DB0
                E7CA2FA1-0DD3-417E-99E7-2BC312E8E359
                FDA1DCF4-8538-4455-9B91-D45E5C668F17
    

说明  
\---\---\-----  
将指定的 AppDisk Uid 重新排序，以最大限度降低层排序冲突。

### 示例 2

    $DesktopGroup = Get-BrokerDesktopGroup -Name "My Group"
                Get-AppLibAppDiskAppDNARecommendedOrder -AppDiskUid $DesktopGroup.AppDiskUids
    
                F92EB804-ECB1-4D45-80C0-610AB3FB7DB0
                E7CA2FA1-0DD3-417E-99E7-2BC312E8E359
                FDA1DCF4-8538-4455-9B91-D45E5C668F17
    

说明  
\---\---\-----  
查找属于名为"My group"的桌面组的磁盘，并查找要重新应用于这些磁盘以最大限度降低分层冲突的最佳顺序。