# Get-ConfigProduct

Lists the site's supported product names and codes.

## 语法

    Get-ConfigProduct [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

- [Get-ConfigSite](Get-ConfigSite.html)
- [Set-ConfigSite](Set-ConfigSite.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### PSObject

## 示例

### 示例 1

    C:\PS> Get-ConfigProduct
    

Description  
\---\---\-----  
Lists the supported products by name and code.