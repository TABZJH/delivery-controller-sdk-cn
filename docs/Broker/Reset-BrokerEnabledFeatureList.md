# Reset-BrokerEnabledFeatureList

Resets the broker's list of enabled features.

## 语法

    Reset-BrokerEnabledFeatureList [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Reset-BrokerLicensingConnection cmdlet resets the broker's list of enabled features.

Toggling site features on or off doesn't become effective immediately. There will typically be a delay as the changes are propagated across the site based on the scheduling of refresh logic built into the controllers.

After toggling features on or off you can run Reset-BrokerEnabledFeatureList to ensure that the broker can access the new list of enabled features immediately.

Each broker service instance holds its list of enabled features. In order for the feature list changes to be applied immediately throughout the XenDesktop site this command needs to be run on every controller in the site.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### 无

## 示例

### 示例 1

    C:\PS> Reset-BrokerEnabledFeatureList
    

Description  
\---\---\-----  
Reset the broker's list of enabled features.