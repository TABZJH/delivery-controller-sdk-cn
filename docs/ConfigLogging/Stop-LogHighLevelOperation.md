# Stop-LogHighLevelOperation

Logs the completion of a previously started high level operation.

## 语法

    Stop-LogHighLevelOperation -HighLevelOperationId <String> -IsSuccessful <Boolean> [-EndTime <DateTime>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Stop-LogHighLevelOperation logs the completion of a started high level operation.

## 相关命令

- [Start-LogHighLevelOperation](Start-LogHighLevelOperation.html)
- [Get-LogHighLevelOperation](Get-LogHighLevelOperation.html)

## 参数

| 名称                   | 说明                                                                    | 是否必需？ | 管道输入  | 默认值                                   |
| -------------------- | --------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| HighLevelOperationId | Specifies the identifier of the high level operation being completed. | true  | false |                                       |
| IsSuccessful         | Specifies if the started high level operation completed sucessfully.  | true  | false |                                       |
| EndTime              | Specifies the end time of the high level operation being completed.   | false | false | DateTime.UtcNow.                      |
| AdminAddress         | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。            | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    C:\PS> $succeeded = $false #indicates if high level operation succeeded.
    C:\PS> # Log high level operation start.
    C:\PS> $highLevelOp = Start-LogHighLevelOperation -Text "Create unmanaged catalog" -Source "My Custom Script"
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