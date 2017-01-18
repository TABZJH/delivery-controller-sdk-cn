# Add-SfServerToCluster

Adds a new server to an existing cluster.

## 语法

    Add-SfServerToCluster -ClusterId <Guid> -ServerName <String> [-StorefrontUrl <Uri>] [-FarmName <String>] [-XmlServices <Uri[]>] [-RunAsynchronously <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Adds a new server to an existing cluster. Optionally updates Farm and Storefront Url. After operation succeeds, all servers are configured identically.

## 相关命令

- [Get-SfCluster](Get-SfCluster.html)
- [New-SfCluster](New-SfCluster.html)
- [Remove-SfServerFromCluster](Remove-SfServerFromCluster.html)
- [Set-SfCluster](Set-SfCluster.html)

## 参数

| 名称                | 说明                                                                                                                                                                                                                                    | 是否必需？ | 管道输入  | 默认值                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ClusterId         | The id of the cluster to perform operation on.                                                                                                                                                                                        | true  | false |                                       |
| 服务器名称             | The name of the server to join to exisiting cluster. The name must be one of the values returned by Get-SfCluster                                                                                                                     | true  | false |                                       |
| StorefrontUrl     | The url that will be used by Receivers to contact Storefront. Http or https absolute urls are accepted.                                                                                                                               | false | false | Server name and http binding.         |
| FarmName          | Name of the farm that will be used within Store service. Either both FarmName and XmlServices need to be specified or none of them.                                                                                                   | false | false |                                       |
| XmlServices       | Collection of the url of xml services that will be used inside a farm. The urls neeed to be http or https, be absolute and share the same schema and port. Either both FarmName and XmlServices need to be specified or none of them. | false | false |                                       |
| RunAsynchronously | If set, the command will run asynchronously.                                                                                                                                                                                          | false | false | false                                 |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                | false | false |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                            | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Storefront.Sdk.Task or Citrix.Storefront.DataModel.Cluster

Returns cluster description or a task, if ran asynchronously.

## 示例

### 示例 1

    Add-SfServerToCluster -ClusterId (Guid) -ServerName NewSfServer -RunAsynchronously $true
    

Description  
\---\---\-----  
Adds "NewSfServer" to cluster with id (Guid).