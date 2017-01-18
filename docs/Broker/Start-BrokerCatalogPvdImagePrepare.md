# Start-BrokerCatalogPvdImagePrepare

Start the PVD Image prepare process in the Broker for the machines in the specified catalog(s).

## 语法

    Start-BrokerCatalogPvdImagePrepare [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Start-BrokerCatalogPvdImagePrepare cmdlet instructs the Broker to request the Personal VDisk (PVD) preparation process for all of the machines in the specified catalog(s). The process begins when each machine is subsequently powered off, at which point brokering of user desktop sessions is suspended as well as regular machine power operations until the process completes. Only catalogs with a PersistUserChanges value of OnPvd are supported by this cmdlet.

## 相关命令

- [Start-BrokerMachinePvdImagePrepare](Start-BrokerMachinePvdImagePrepare.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The catalog(s) holding the machines on which to start the PVD Image Preparation process.                                                                                        | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Catalog

You can pipe in the catalogs on which to start the PVD image preparation process.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Get-BrokerCatalog 'MyCatalog' | Start-BrokerCatalogPvdImagePrepare
    

Description  
\---\---\-----  
Instruct the Broker that the Personal VDisk preparation process will start the next time the machines in the specified catalog are powered off.