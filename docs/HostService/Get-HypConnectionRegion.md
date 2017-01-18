# Get-HypConnectionRegion

Enumerates the regions of a hypervisor connection that are based on cloud technology.

## 语法

    Get-HypConnectionRegion [-LiteralPath] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to enumerate the available regions within a public or private cloud, when making hypervisor connections to cloud services. Sometimes, regions need to be selected and applied before the cloud connection can be used in a meaningful way. This cmdlet allows the supported regions to be listed so that one may be selected.

Once a region has been chosen, use the standard Set-Item provider cmdlet to select it. See the examples for further details.

This cmdlet may return no output, in which case the cloud connection can be considered "regionless" (or, implicitly, all within a single region). In such cases, there is no need to select a region, and the hypervisor connection can be used as is.

## 相关命令

- [Set-Item](Set-Item.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入           | 默认值                                  |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------ |
| LiteralPath  | Specifies the path to the hypervisor connection whose regions are being examined. This cmdlet is valid only for hypervisor connections that have the UsesCloudInfrastructure flag set to true. The path must be in one of the following formats: <drive>:\Connections\<connectionname> 或者 <drive>:\Connections\{<connection uid>} | true  | true (ByValue) |                                      |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide a host name or an IP address.                                                                                                                                                                                              | false | false          | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Get-HypConnectionRegion (LiteralPath parameter).

## 返回值

### Citrix.Host.Sdk.HypervisorRegion

Get-HypConnectionRegion returns zero or more instances of the HypervisorConnectionRegion object, each of which contain the following properties:  
名称 <string> Specifies the unique name of the region. Endpoint <string> Specifies the URL endpoint that is specific to the region, if relevant. This may be an empty string, and is returned only for information purposes.  
A full list of the hypervisor networks that are exposed for use in the hosting unit.## Notes In the case of failure, the following errors can be produced.  
错误代码  
\---\---\-----  
ConnectionsPathInvalid  
The path provided is not to an item in the Connections subdirectory of the host service provider.  
HypervisorConnectionObjectNotFound  
The path provided could not be resolved to an existing hypervisor connection. The name or GUID is invalid.  
HypervisorInMaintenanceMode  
The hypervisor for the connection is in maintenance mode.  
ConnectionIsNotCloud  
The hypervisor connection is not associated with cloud infrastructure, making it invalid to enumerate regions.  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
An error occurred in the service while attempting a database operation. Communication with the database failed for  
various reasons.  
CommunicationError  
与服务通信时发生错误。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## 示例

### 示例 1

    c:\PS>Get-HypConnectionRegions -LiteralPath XDHyp:\Connections\AWS
    
              RegionName           : us-east-1
              Endpoint             : ec2.us-east-1.amazonaws.com
    
              RegionName           : us-west-1
              Endpoint             : ec2.us-west-1.amazonaws.com
    
              RegionName           : eu-west-1
              Endpoint             : ec2.eu-west-1.amazonaws.com
    
              (...)
    
              c:\PS>Set-Item -Path XDHyp:\Connections\AWS -Region "us-east-1"
    

Description  
\---\---\-----  
This sequence of commands enumerates the available regions of an Amazon AWS cloud connection, and then selects one of them for use in the connection.