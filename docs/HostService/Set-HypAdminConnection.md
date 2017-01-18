# Set-HypAdminConnection

Set the controller to be used by the cmdlets that form the Host service PowerShell snap-in.

## 语法

    Set-HypAdminConnection [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to set the default controller address to be used by the cmdlets to communicate with the controller. Most Host service cmdlets take an 'AdminAddress' parameter that can be used to define the controller (when used, this overrides this setting). However, the Set-Location cmdlet in the Host service provider does not offer this option. Therefore, the controller address must be set using this cmdlet, if no other cmdlets have set the address previously in the current runspace.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ----- | ------------------------------------- |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address. | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 示例

### 示例 1

    c:\PS>Set-HypAdminConnection -AdminAddress myserver.com
    

Description  
\---\---\-----  
This command sets the controller address for the commands to be "myserver.com". All commands run use this address until it is altered, either by another call to this command or by the use of the 'AdminAddress' parameter in another command in the Host service snap-in.