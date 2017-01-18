# Get-SfCluster

Gets all Storefront clusters present in the site.

## 语法

    Get-SfCluster [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets all Storefront clusters present in the site. There is one special Cluster with null id that lists the servers that are not part to any cluster (they are available to join any).

## 相关命令

- [New-SfCluster](New-SfCluster.html)
- [Add-SfServerToCluster](Add-SfServerToCluster.html)
- [Remove-SfServerFromCluster](Remove-SfServerFromCluster.html)
- [Set-SfCluster](Set-SfCluster.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Storefront.DataModel.Cluster[]

Returns array of clusters available in current deployment.

## 示例

### 示例 1

    <br />

说明  
\---\---\-----