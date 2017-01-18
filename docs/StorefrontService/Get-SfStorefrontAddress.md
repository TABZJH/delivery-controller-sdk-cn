# Get-SfStorefrontAddress

Gets the high-level description of a configuration for StoreFront addresses, based on a configuration byte array.

## 语法

    Get-SfStorefrontAddress [-ByteArray] <Byte[]> [<CommonParameters>]
    

## 详细说明

Use this command to convert a configuration byte array into a set of named property settings. The byte array will either have been retrieved from the Citrix Broker Service, or from the New-SfStorefrontAddress cmdlet.

## 相关命令

- [New-SfStorefrontAddress](New-SfStorefrontAddress.html)
- [Add-SfStorefrontAddress](Add-SfStorefrontAddress.html)
- [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
- [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)
- [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)

## 参数

| 名称        | 说明                                                           | 是否必需？ | 管道输入           | 默认值 |
| --------- | ------------------------------------------------------------ | ----- | -------------- | --- |
| ByteArray | Specifies the low-level byte array (blob) to be interpreted. | true  | true (ByValue) |     |

## 输入类型

### System.Byte[]

The cmdlet accepts the ByteArray parameter as pipeline input.

## 返回值

### Citrix.Storefront.Sdk.SfStorefrontAddress

This cmdlet outputs one SfStorefrontAddress object for each address that is configured within the slot. Each object has the following properties:  
Name - Specifies the name of the StoreFront.  
Url - Specifies the URL to the StoreFront, such as "https://mysite.com/Citrix/StoreWeb".  
Enabled - Specifies whether the StoreFront is enabled for users.  
Description - Specifies the human-readable name of the StoreFront.

## 示例

### 示例 1

    C:\PS> $configuration = New-SfStorefrontAddress -Url "https://mysite.com/Citrix/StoreWeb" -Description "This StoreFront delivers my corporate applications" -Name "StoreFront1" -Enabled $true
    
    C:\PS> Get-SfStorefrontAddress -ByteArray $configuration
    
    Name               Url                                       Enabled Description
    ----               ---                                       ------- -----------
    StoreFront1        https://mysite.com/Citrix/StoreWeb           True This StoreFront delivers my corporate applications.
    

Description  
\---\---\-----  
This example shows a new configuration byte array being created to specify a single StoreFront address. The configuration byte array is then provided as input to the Get-SfStorefrontAddress command, which interprets and outputs the same fields.