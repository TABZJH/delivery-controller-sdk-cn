# Send-BrokerSessionMessage

Sends a message to a session.

## 语法

    Send-BrokerSessionMessage [-InputObject] <Session[]> [-MessageStyle] <SendMessageStyle> [-Title] <String> [-Text] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Generates a message box in the target session(s).

## 相关命令

- [Get-BrokerSession](Get-BrokerSession.html)

## 参数

| 名称           | 说明                                                                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                                                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | -------------------------------------------------------------------------------------- |
| InputObject  | The target session(s) to send the message to.                                                                                                                                   | true  | true (ByValue) |                                                                                        |
| MessageStyle | The style of message box to use (valid values are Critical, Question, Exclamation, or Information).                                                                             | true  | true (ByValue) |                                                                                        |
| 标题           | Text to display in the messagebox title bar.                                                                                                                                    | true  | true (ByValue) |                                                                                        |
| 文本           | The message to display.                                                                                                                                                         | true  | true (ByValue) |                                                                                        |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false          |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                              | false | false          | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### Citrix.Broker.Admin.SDK.Session

The session to which to send the message can be piped in.

## 返回值

### 无

## Notes Sessions can be passed as the InputObject parameter as either session objects or their numeric Uids.  
This operation is non-blocking and returns before it completes. The operation, however, is unlikely to fail unless there are communication problems between controller and machine, if bad arguments are passed to the cmdlet itself or if the machine cannot successfully execute the operation.  
The transient nature of sessions means that the list of session objects or UIDs supplied to Send-BrokerSessionMessage could consist of valid and invalid sessions. Invalid sessions are detected and disregarded and the send message operation is invoked on the machines running valid sessions.  
The system can fail to invoke the operation if the machine is not in an appropriate state or if there are problems in communicating with the machine. When an operation is invoked the system detects if the operation was initiated successfully or not by the session. As this operation is non-blocking the system doesn't detect or report whether the operation ultimately succeeded or failed after its successful initialization in the session.  
Operation failures are reported through the broker SDK error handling mechanism (see about_Broker_ErrorHandling). In the event of errors the SdkErrorRecord error status code is set to SessionOperationFailed and its error data dictionary is populated with the following entries:  
o OperationsAttemptedCount: The number of operations attempted.  
o OperationsFailedCount - The number of failed operations.  
o OperationsSucceededCount - The number of successfully executed operations.  
o UnresolvedSessionFailuresCount - The number of operations that failed due to invalid sessions being supplied.  
o OperationInvocationFailuresCount - The number of operations that failed because they could not be invoked in the session.  
o DesktopExecutionFailuresCount - The number of operations that failed because they could not be successfully executed in the session.  
The SdkErrorRecord message will also display the number of attempted, failed and successful operations in the following format:  
"Session operation error - attempted:<operationsattemptedcount>, failed:<operationsfailedcount>, succeeded:<operationssucceededcount>"

## 示例

### 示例 1

    C:\PS> $sessions = Get-BrokerSession -UserName MYDOMAIN\*
    C:\PS> Send-BrokerSessionMessage $sessions -MessageStyle Information -Title TestTitle -Text TestMessage
    

Description  
\---\---\-----  
Sends a message to all the sessions for any user in MYDOMAIN.

### 示例 2

    C:\PS> $desktop = Get-BrokerDesktop -Uid 1
    C:\PS> Send-BrokerSessionMessage $desktop.SessionUid -MessageStyle Information -Title TestTitle -Text TestMessage
    

Description  
\---\---\-----  
Sends a message to the session on the desktop with Uid 1.

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
    C:\PS> Send-BrokerSessionMessage -InputObject 10,11,12 -MessageStyle Information -Title "message title" -Text "message text"
    

Description  
\---\---\-----  
Trap and display error information.