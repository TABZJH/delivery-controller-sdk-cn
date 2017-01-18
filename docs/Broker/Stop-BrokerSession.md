# Stop-BrokerSession

Stop or log off a session.

## 语法

    Stop-BrokerSession [-InputObject] <Session[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Stops or logs off sessions.

## 相关命令

- [Disconnect-BrokerSession](Disconnect-BrokerSession.html)
- [Get-BrokerSession](Get-BrokerSession.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Identifies the session(s) to terminate. This can be expressed as either a session Uid or a session object.                                                                      | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Session

The sessions to stop can be piped into this cmdlet.

## 返回值

### 无

## Notes This operation is non-blocking and returns before it completes. The operation, however, is unlikely to fail unless there are communication problems between the controller and the machine, if bad arguments are passed to the cmdlet itself or if the machine cannot successfully execute the operation.  
The transient nature of sessions means that the list of session objects or UIDs supplied to Stop-BrokerSession could consist of valid and invalid sessions. Invalid sessions are detected and disregarded and the stop session operation is invoked on the valid sessions.  
The system can fail to invoke the operation if the machine is not in an appropriate state or if there are problems in communicating with the machine. When an operation is invoked the system detects if the operation was initiated successfully or not by the machine. As this operation is non-blocking the system doesn't detect or report whether the operation ultimately succeeded or failed after its successful initialization on the machine.  
Operation failures are reported through the broker SDK error handling mechanism (see about_Broker_ErrorHandling). In the event of errors the SdkErrorRecord error status is set to SessionOperationFailed and its error data dictionary is populated with the following entries:  
o OperationsAttemptedCount - The number of operations attempted.  
o OperationsFailedCount - The number of failed operations.  
o OperationsSucceededCount - The number of successfully executed operations.  
o UnresolvedSessionFailuresCount - The number of operations that failed due to invalid sessions being supplied.  
o OperationInvocationFailuresCount - The number of operations that failed because they could not be invoked on the desktop.  
o DesktopExecutionFailuresCount - The number of operations that failed because they could not be successfully executed by the desktop.  
The SdkErrorRecord message will also display the number of attempted, failed and successful operations in the following format:  
"Session operation error - attempted:<operationsattemptedcount>, failed:<operationsfailedcount>, succeeded:<operationssucceededcount>"

## 示例

### 示例 1

    C:\PS> Get-BrokerSession -UserName MyDomain\MyAccount | Stop-BrokerSession
    

Description  
\---\---\-----  
Stops all sessions for the user MyDomain\MyAccount.

### 示例 2

    C:\PS> $desktop = Get-BrokerDesktop -DNSName MyMachine.MyDomain.com
    C:\PS> Stop-BrokerSession $desktop.SessionUid
    

Description  
\---\---\-----  
Stops the session on MyMachine.

### 示例 3

    C:\PS> Get-BrokerSession -Filter { SessionState -eq 'Disconnected' -and SessionStateChangeTime -lt '-1' } | Stop-BrokerSession
    

Description  
\---\---\-----  
Stop sessions that have been disconnected for more than one day.

### 示例 4

    C:\PS> trap  [Citrix.Broker.Admin.SDK.SdkOperationException]
    C:\PS> {
    C:\PS>   write $("Exception name = " + $_.Exception.GetType().FullName)
    C:\PS>   write $("SdkOperationException.Status = " + $_.Exception.Status)
    C:\PS>   write $("SdkOperationException.ErrorData=")
    C:\PS>   $_.Exception.ErrorData
    C:\PS>
    C:\PS>   write $("SdkOperationException.InnerException = " + $_.Exception.InnerException)
    C:\PS>   $_.Exception.InnerException
    C:\PS>   continue
    C:\PS> }
    C:\PS>
    C:\PS> Stop-BrokerSession -InputObject 10,11,12
    

Description  
\---\---\-----  
Trap and display error information.