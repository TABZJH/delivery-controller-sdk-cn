# Start-BrokerMachinePvdImagePrepare

Start the PVD Image prepare process in the Broker for the specified machine(s).

## 语法

    Start-BrokerMachinePvdImagePrepare [-InputObject] <Machine[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Start-BrokerMachinePvdImagePrepare cmdlet instructs the Broker to request the Personal VDisk (PVD) preparation process for the specified machine(s). The process begins when each machine is subsequently powered off, at which point brokering of user desktop sessions is suspended as well as regular machine power operations until the process completes. Only machines in catalogs with a PersistUserChanges value of OnPvd are supported by this cmdlet.

## 相关命令

- [Start-BrokerCatalogPvdImagePrepare](Start-BrokerCatalogPvdImagePrepare.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The machine(s) to start the PVD Image Preparation process on.                                                                                                                   | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Machine

You can pipe in the machines to start the PVD image preparation process on.

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Get-BrokerMachine 'MyMachine' | Start-BrokerMachinePvdImagePrepare
    

Description  
\---\---\-----  
Instruct the Broker that the Personal VDisk preparation process will start the next time the specified machine(s) are powered off.