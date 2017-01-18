# Get-ConfigLocalData

Gets the service local data.

## 语法

    Get-ConfigLocalData [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Get-ConfigLocalData returns service-and-controller-specific local data. This information is not site-wide, but rather controller-specific. The Configuration Service currently stores the controller product version as local data. The overall site version used by Studio is an aggregate of the product versions from each controller.

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

This cmdlet does not accept pipeline input

## 返回值

### Citrix.Configuration.DataModel.LocalData

Contains the ControllerProductVersion field

## 示例

### 示例 1

    C:\PS> Get-ConfigLocalData
    
    ControllerProductVersion
    -----------
    7.1
    

Description  
\---\---\-----  
Gets the service local data.