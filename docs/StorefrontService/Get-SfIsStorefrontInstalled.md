# Get-SfIsStorefrontInstalled

Tells whether StoreFront Services and Privileged Service are installed.

## 语法

    Get-SfIsStorefrontInstalled [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 布尔型

True if both StoreFront Services and Privileged Service are installed, false otherwise.

## 示例

### 示例 1

    <br />

说明  
\---\---\-----