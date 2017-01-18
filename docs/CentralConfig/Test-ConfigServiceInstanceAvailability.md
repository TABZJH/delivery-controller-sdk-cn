# Test-ConfigServiceInstanceAvailability

Tests whether the supplied service instances are responding to requests.

## 语法

    Test-ConfigServiceInstanceAvailability [-ServiceInstance] <ServiceInstance[]> [-MaxDelaySeconds <Int32>] [-ForceWaitForOneOfEachType] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

- [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
- [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance.html)
- [Get-ConfigRegisteredServiceInstance](Get-ConfigRegisteredServiceInstance.html)

## 参数

| 名称                        | 说明                                                                                                | 是否必需？ | 管道输入           | 默认值                                                                                        |
| ------------------------- | ------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------------------------------------------------------------ |
| ServiceInstance           | The service instances to test.                                                                    | true  | true (ByValue) |                                                                                            |
| MaxDelaySeconds           | The timeout period to wait before concluding that services are unresponsive.                      | false | false          | Infinite                                                                                   |
| ForceWaitForOneOfEachType | If at least one of each type of service responds, finish immediately.                             | false | false          |                                                                                            |
| AdminAddress              | Specifies the host name or IP address of the controller to which the PowerShell snap-in connects. | false | false          | 'LocalHost'. Once a value is specified by any command, this value becomes the new default. |

## 输入类型

### 

## 返回值

### System.Management.Automation.PSObject  
This represents a service instance and has the following parameters;  
ServiceGroupUid <guid>  
The unique identifer for the service group to which the service instance belongs.  
ServiceGroupName <string>  
The name of the service group that the service instance is part of.  
ServiceInstanceUid <guid>  
The unique identifier for the service instance.  
ServiceType <string>  
The type of the service group.  
Address <string>  
The contact address for the service instance.  
Binding <string>  
The binding to use for connections to the service instance.  
Version <int>  
The version of the service instance.  
ServiceAccount <string>  
The AD computer account for the computer that is providing the service instance.  
ServiceAccountSid <string>  
The AD computer account SID for the computer that is providing the service instance.  
InterfaceType <string>  
The interface type for the service instance.  
Metadata <Citrix.Configuration.Sdk.Metadata[]>  
The metadata for the service instance.  
Status <Citrix.Configuration.Sdk.Commands.Availability>  
An enumeration value indicating whether the service is Responding, NotResponding, Unknown, or BadBindingType.  
ResponseTime <System.TineSpan>  
The interval elapsed between hailing the service and getting a definite response

## Notes The Availability Status Codes are o Responding: Got a positive response o NotResponding: Got a response, but it was negative or the connection was refused o Unknown: Did not respond in time / timed-out o BadBindingType: Binding parameter in ServiceInstance is not wcf_HTTP_kerb

## Examples

### EXAMPLE 1

    C:\>Get-ConfigRegisteredServiceInstance | Test-ConfigServiceInstanceAvailability -ForceWaitForOneOfEachType
    

Description  
\---\---\-----  
Test all the service instances that are registered in the Configuration Service, returning when one of each type is responding.

### EXAMPLE 2

    C:\>Test-ConfigServiceInstanceAvailability -ServiceInstance $services -MaxDelaySeconds 5
    

Description  
\---\---\-----  
Test each of the given services, allowing a 5 second time-out.