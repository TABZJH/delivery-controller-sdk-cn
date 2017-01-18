# Disconnect-BrokerSession

Disconnect a session.

## 语法

    Disconnect-BrokerSession [-InputObject] <Session[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Disconnects the specified session.

If the session is active, no warning is issued to the user before that session is disconnected.

After disconnection, sessions enter a Disconnected state. In a Disconnected state, a session still exists but there is no remote connection to that session.

## 相关命令

- [Get-BrokerSession](Get-BrokerSession.html)
- [Stop-BrokerSession](Stop-BrokerSession.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | Identifies the session(s) to disconnect. This can be expressed as either a session Uid or a session object.                                                                     | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Session

The sessions to disconnect can be piped into this cmdlet.

## 返回值

### 无

## Notes This operation is non-blocking and returns before it completes. The operation, however, is unlikely to fail unless there are communication problems between the controller and the machine, or if bad arguments are passed to the cmdlet itself or if the machine cannot successfully execute the operation.  
The transient nature of sessions means that the list of session objects or UIDs supplied to Disconnect-BrokerSession could consist of valid and invalid sessions. Invalid sessions are detected and disregarded and the disconnect session operation is invoked on only the valid sessions.  
The system can fail to disconnect the session if the machine is not in an appropriate state or if there are problems in communicating with the machine. When a disconnect is requested the system detects if the operation was initiated successfully or not by the machine. As this operation is non-blocking the system doesn't detect or report whether the disconnect ultimately succeeded or failed after it was started.  
Disconnect failures are reported through the broker SDK error handling mechanism (see about_Broker_ErrorHandling). In the event of errors the SdkErrorRecord error status is set to SessionOperationFailed and its error data dictionary is populated with the following entries:  
o OperationsAttemptedCount: The number of operations attempted.  
o OperationsFailedCount - The number of failed operations.  
o OperationsSucceededCount - The number of successfully executed operations.  
o UnresolvedSessionFailuresCount - The number of operations that failed due to invalid sessions being supplied.  
o OperationInvocationFailuresCount - The number of operations that failed because they could not be invoked on the machine.  
o DesktopExecutionFailuresCount - The number of operations that failed because they could not be successfully executed by the machine.  
The SdkErrorRecord message will also display the number of attempted, failed and successful operations in the following format:  
"Session operation error - attempted:<operationsattemptedcount>, failed:<operationsfailedcount>, succeeded:<operationssucceededcount>"

## 示例

### 示例 1

    C:\PS> Get-BrokerSession -UserName MyDomain\MyAccount | Disconnect-BrokerSession
    

Description  
\---\---\-----  
Attempts to disconnect all of the sessions for the user MyDomain\MyAccount.

### 示例 2

    C:\PS> $desktop = Get-BrokerDesktop -DNSName MyMachine.MyDomain.com
    C:\PS> Disconnect-BrokerSession $desktop.SessionUid
    

Description  
\---\---\-----  
Disconnects the session on MyMachine.

### 示例 3

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
    C:\PS> Disconnect-BrokerSession -InputObject 10,11,12
    

Description  
\---\---\-----  
Attempts to disconnect sessions 10, 11 and 12. Traps and displays the error information.