# Start-LogHighLevelOperation

Logs the start of a high level operation.

## 语法

    Start-LogHighLevelOperation -Text <String> -Source <String> [-StartTime <DateTime>] [-OperationType <OperationType>] [-TargetTypes <String[]>] [-Parameters <Hashtable>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Start-LogHighLevelOperation creates a log entry to record the start of a high level operation.

Start-LogHighLevelOperation can be called to log high level configuration changes which originate from customized configuration scripts. Start-LogHighLevelOperation should be called before the script invokes service SDK cmdlets which execute the configuration changes.

Start-LogHighLevelOperation returns a HighLevelOperation object which contains information about the started high level operation. The "Id" property of the returned HighLevelOperation uniquely identifies the started high level operation. This can be supplied into the "-LoggingId" parameter which is implemented in all service SDK cmdlets which execute loggable configuration changes.

High level operation logs are automatically created by the XenDesktop consoles when: o Initiating an operation which performs configuration changes. o Initiating an operation which performs an administration activity.

## Configuration Change and Administrator Activity

A configuration change is an operation which alters the configuration of the XenDesktop site. Examples of a configuration changes include: o Creating or editing a host. o Creating or editing a catalog. o Adding a user to a delivery group. o Deleting a machine. An administrator activity operation doesn't directly alter site configuration, but it could be an operation carried out by an administrator as part of site management or helpdesk support. Examples of administrator activities include: o Shutdown/start/restart of a user desktop. o Studio or Director sending a message to a user. o Rebooting a user's desktop. Once the change being logged has completed (whether successfully or not) the Stop-LogHighLevelOperation cmdlet should be called to log the completion of a started high level operation.

## 相关命令

- [Stop-LogHighLevelOperation](Stop-LogHighLevelOperation.html)
- [Get-LogHighLevelOperation](Get-LogHighLevelOperation.html)

## 参数

| 名称            | 说明                                                                                                                                                                                                                                           | 是否必需？ | 管道输入  | 默认值                                   |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 文本            | Specifies text to describe the high level operation.                                                                                                                                                                                         | true  | false |                                       |
| 源             | Specifies the source of the high level operation.                                                                                                                                                                                            | true  | false |                                       |
| StartTime     | Specifies the start time of the high level operation.                                                                                                                                                                                        | false | false | DateTime.UtcNow                       |
| OperationType | Specifies the type of operation being logged. Values can be:  
o AdminActivity - If the operation being logged performs an administration activity.  
o ConfigurationChange - If the operation being logged performs a configuration change. | false | false | ConfigurationChange                   |
| TargetTypes   | Specifies the names of the object types that will be affected by the operation being logged.                                                                                                                                                 | false | false |                                       |
| 参数            | Specifies the names and values of parameters that are supplied to the operation being logged.                                                                                                                                                | false | false |                                       |
| AdminAddress  | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                   | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ConfigurationLogging.Sdk.HighLevelOperation

The newly logged high level operation start.

## 示例

### 示例 1

    C:\PS> $succeeded = $false #indicates if high level operation succeeded.
    C:\PS> # Log high level operation start.
    C:\PS> $highLevelOp = Start-LogHighLevelOperation -Text "Create catalog" -Source "My Custom Script"
    C:\PS>
    C:\PS> try
    C:\PS> {
    C:\PS>   # Create catalog object
    C:\PS>   $catalog = New-BrokerCatalog -Name "MyCatalog" -ProvisioningType Manual -AllocationType Permanent -MinimumFunctionalLevel 'LMAX' -LoggingId $highLevelOp.Id
    C:\PS>
    C:\PS>   # Add a machine to the catalog
    C:\PS>   $machine = New-BrokerMachine -CatalogUid $catalog.Uid -MachineName "DOMAIN\Machine" -LoggingId $highLevelOp.Id
    C:\PS>   $succeeded = $true
    C:\PS> }
    C:\PS> catch{ "Error encountered" }
    C:\PS>
    C:\PS> finally{
    C:\PS>   # Log high level operation stop, and indicate its success
    C:\PS>   Stop-LogHighLevelOperation -HighLevelOperationId $highLevelOp.Id -IsSuccessful $succeeded
    C:\PS> }
    

Description  
\---\---\-----  
Creates an unmanaged catalog and assigns a machine to it, within the scope of a high level operation start and stop. The identifier of the high level operation is passed into the "-LoggingId" parameter of the service SDK cmdlets. The execution of the cmdlets in the services will create the low level operation logs for the supplied high level operation.