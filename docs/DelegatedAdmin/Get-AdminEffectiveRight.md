# Get-AdminEffectiveRight

Gets the set of Right objects associated with the current user.

## 语法

    Get-AdminEffectiveRight [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Get-AdminEffectiveRight cmdlet returns the effective rights of the current user. This is the union of all rights of the enabled administrators that the current user matches, taking into account Active Directory group membership.

## 相关命令

- [Get-AdminAdministrator](Get-AdminAdministrator.html)
- [Add-AdminRight](Add-AdminRight.html)
- [Remove-AdminRight](Remove-AdminRight.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.DelegatedAdmin.Sdk.Right

The Rights associated with the current user

## 示例

### 示例 1

    C:\PS> Get-AdminEffectiveRight
    

Description  
\---\---\-----  
Return the effective rights for the current user.