# Get-BrokerController

Gets Controllers running broker services in the site.

## 语法

    Get-BrokerController [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-BrokerController [[-MachineName] <String>] [-ControllerVersion <String>] [-DesktopsRegistered <Int32>] [-DNSName <String>] [-LastActivityTime <DateTime>] [-LastLicensingServerEvent <LicensingServerEvent>] [-LastLicensingServerEventTime <DateTime>] [-LastStartTime <DateTime>] [-LicensingGraceState <LicensingGraceState>] [-LicensingServerState <LicensingServerState>] [-Metadata <String>] [-OSType <String>] [-OSVersion <String>] [-SID <String>] [-State <ControllerState>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets Controllers from the current site that match the specified search criteria.

Controllers are server machines running instances of the broker service. The broker service is responsible for the brokering of user sessions to desktops or applications, and for power management of the underlying machines. An operational site must contain at least one Controller.

If no search criteria are specified, all Controllers in the site are obtained.

\---\---\---\---\---\---\---\----- BrokerController Object The BrokerController object represents a single controller running an instance of the Broker service. It contains the following properties:

    -- ActiveSiteServices (System.String[])
       The Broker site services active on the controller.
    
    -- AssociatedHypervisorConnectionUids (System.Int32[])
       The UIDs of the hypervisor connections being managed by the Broker service on the controller.
    
    -- ControllerVersion (System.String)
       The version of the Broker service on the controller.
    
    -- DesktopsRegistered (System.Int32)
       The number of VDA machines registered with the Broker service on the controller.
    
    -- DNSName (System.String)
       The DNS name of the controller.
    
    -- LastActivityTime (System.DateTime?)
       The last reported activity time of the Broker service on the controller.
    
    -- LastLicensingServerEvent (Citrix.Broker.Admin.SDK.LicensingServerEvent?)
       Last significant licensing server event reported by the Broker service on the controller.
    
    -- LastLicensingServerEventDetails (System.String[])
       Additional details associated with the last significant licensing server event.
    
    -- LastLicensingServerEventTime (System.DateTime?)
       Time at which the last significant licensing server event was reported.
    
    -- LastStartTime (System.DateTime?)
       The last start-up time of the Broker service on the controller.
    
    -- LicensingGracePeriodReasons (Citrix.Broker.Admin.SDK.LicensingGracePeriodReason[])
       Current active or expired licensing grace periods in effect on the controller.
    
    -- LicensingGracePeriodTimesRemaining (System.TimeSpan[])
       Times remaining in currently active or expired licensing grace periods in effect on the controller. Expired grace periods are indicated by zero remaining time. The number and order of entries in this list matches that in the LicensingGracePeriodReasons list.
    
    -- LicensingGraceState (Citrix.Broker.Admin.SDK.LicensingGraceState)
       The licensing grace state currently in effect in the Broker service on the controller.
    
    -- LicensingServerState (Citrix.Broker.Admin.SDK.LicensingServerState)
       The licensing server state currently in effect in the Broker service on the controller.
    
    -- MachineName (System.String)
       The Windows name of the controller.
    
    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       The metadata for the controller.
    
    -- OSType (System.String)
       The Operating System type of the controller.
    
    -- OSVersion (System.String)
       The Operating System version of the controller.
    
    -- SID (System.String)
       The SID of the controller.
    
    -- State (Citrix.Broker.Admin.SDK.ControllerState)
       The state of the Broker service on the controller.
    
    -- Uid (System.Int32)
       The UID of the controller instance.
    
    -- UUID (System.Guid)
       A globally unique identifier of the controller instance.
    

## 相关命令

- [Get-BrokerDesktop](Get-BrokerDesktop.html)

## 参数

| 名称                           | 说明                                                                                                                                                                                            | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| UID                          | Gets only Controller with the specified unique ID.                                                                                                                                            | true  | false |                                                                                        |
| MachineName                  | Gets only Controllers with the specified Windows name. ('domain\machine')                                                                                                                    | false | false |                                                                                        |
| ControllerVersion            | Gets only Controllers running the specified version of the broker service.                                                                                                                    | false | false |                                                                                        |
| DesktopsRegistered           | Gets only Controllers that have the specified number of desktops currently registered. This parameter is mainly of use with advanced filtering; see about_Broker_Filtering.                 | false | false |                                                                                        |
| DNSName                      | Gets only Controllers with the specified DNS name ('machine.domain')                                                                                                                          | false | false |                                                                                        |
| LastActivityTime             | Gets only Controllers last reported as active at the specified time. This parameter is mainly of use with advanced filtering; see about_Broker_Filtering.                                   | false | false |                                                                                        |
| LastLicensingServerEvent     | Gets only Controllers with the specified last license server event recorded.                                                                                                                  | false | false |                                                                                        |
| LastLicensingServerEventTime | Gets only Controllers with its last recorded licensing server event at the specified time. This parameter is mainly of use with advanced filtering; see about_Broker_Filtering.             | false | false |                                                                                        |
| LastStartTime                | Gets only Controllers that last started-up at the specified time. This parameter is mainly of use with advanced filtering; see about_Broker_Filtering.                                      | false | false |                                                                                        |
| LicensingGraceState          | Gets only Controllers in the specified licensing grace state.  
Valid values are: NotActive, InOutOfBoxGracePeriod, InSupplementalGracePeriod, InEmergencyGracePeriod and GracePeriodExpired. | false | false |                                                                                        |
| LicensingServerState         | Gets only Controllers in the specified licensing server state. Valid values are: ServerNotSpecified, NotConnected, OK, LicenseNotInstalled, LicenseExpired, Incompatible and Failed.          | false | false |                                                                                        |
| 元数据                          | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                                                                                                     | false | false |                                                                                        |
| OSType                       | Gets only Controllers running the specified Operating System type.                                                                                                                            | false | false |                                                                                        |
| OSVersion                    | Gets only Controllers running the specified Operating System version.                                                                                                                         | false | false |                                                                                        |
| SID                          | Gets only Controllers with the specified SID.                                                                                                                                                 | false | false |                                                                                        |
| 状态                           | Gets only Controllers currently in the specified state.  
Valid values are: Failed, Off, On, and Active.                                                                                      | false | false |                                                                                        |
| UUID                         | Gets only the Controller with the specified GUID.                                                                                                                                             | false | false |                                                                                        |
| ReturnTotalRecordCount       | When specified, this causes the cmdlet to output an error record containing the number of records available. 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Broker_Filtering for details.              | false | false | False                                                                                  |
| MaxRecordCount               | 指定要返回的最大记录数。                                                                                                                                                                                  | false | false | 250                                                                                    |
| 跳过                           | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                         | false | false |                                                                                        |
| SortBy                       | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                      | false | false | 默认排序顺序是按名称或唯一标识符。                                                                      |
| 过滤器                          | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details.                                                                                       | false | false |                                                                                        |
| 属性                           | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                        | false | false |                                                                                        |
| AdminAddress                 | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.                                            | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.Controller

Returns Controllers matching all specified selection criteria.

## 示例

### 示例 1

    C:\PS> Get-BrokerController -State Active
    

Description  
\---\---\-----  
Gets all Controllers in the site that are currently active (powered on and fully operational).

### 示例 2

    C:\PS> Get-BrokerController -Filter 'LastStartTime -gt "-30:00"'
    

Description  
\---\---\-----  
Gets all Controllers in the site that started-up in the last 30 minutes.