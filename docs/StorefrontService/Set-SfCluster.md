# Set-SfCluster

Sets the parameters on the given cluster.

## 语法

    Set-SfCluster -ClusterId <Guid> [-StorefrontUrl <Uri>] [-FarmName <String>] [-XmlServices <Uri[]>] [-RunAsynchronously <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Sets the parameters on the given cluster and propagate the changes to all servers within a given cluster.

## 相关命令

- [Get-SfCluster](Get-SfCluster.html)
- [New-SfCluster](New-SfCluster.html)
- [Add-SfServerToCluster](Add-SfServerToCluster.html)
- [Remove-SfServerFromCluster](Remove-SfServerFromCluster.html)

## 参数

| 名称                | 说明                                                                                                                                                                                                                                    | 是否必需？ | 管道输入  | 默认值                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ClusterId         | The if of the cluster to perform operation on.                                                                                                                                                                                        | true  | false |                                       |
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

    Set-SfCluster -StorefrontUrl http://SfUrl -ClusterId (Guid) -RunAsynchronously $true
    

Description  
\---\---\-----  
Sets a Storefront Url in a Cluster with id (Guid). Propagates changes to all servers that are part of the cluster.