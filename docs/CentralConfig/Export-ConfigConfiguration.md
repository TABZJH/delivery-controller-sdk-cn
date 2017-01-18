# Export-ConfigConfiguration

Obtains an XML document containing the configuration of the Site

## 语法

    Export-ConfigConfiguration [-ExistingConfigLastChangeTime <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

## 参数

| 名称                           | 说明                                                                                                                                                                                                               | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ExistingConfigLastChangeTime | The value of ConfigLastChangeTime in the site object of any configuration already held by the caller. If nothing has changed, an empty configuration will be returned with the "Updated" attribute set to false. | false | false | $null                                 |
| AdminAddress                 | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                       | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### This cmdlet does not accept input

## 返回值

### 字符串

The XML document