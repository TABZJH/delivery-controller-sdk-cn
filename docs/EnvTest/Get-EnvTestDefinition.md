# Get-EnvTestDefinition

Gets the one or more test definitions

## 语法

    Get-EnvTestDefinition [-TestId <String[]>] [-CultureName <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a list of test definitions that are available from currently running components.

## 相关命令

- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Get-EnvTestTask](Get-EnvTestTask.html)
- [Start-EnvTestTask](Start-EnvTestTask.html)
- [Switch-EnvTestTask](Switch-EnvTestTask.html)
- [Stop-EnvTestTask](Stop-EnvTestTask.html)
- [Remove-EnvTestTask](Remove-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称           | 说明                                                                                                                              | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| TestId       | The id of one or more tests.                                                                                                    | false | true (ByValue) |                                       |
| CultureName  | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US". | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                      | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.String

A test id.### System.String[] An array of test ids.

## 返回值

### Citrix.EnvTest.Sdk.EnvTestDefinition

One or more test definitions.

## 示例

### 示例 1

    $allTestDefinitions = Get-EnvTestDefinition
    

Description  
\---\---\-----  
Retrieve all tests.

### 示例 2

    $allTestDefinitionsTranslatedIntoSpanish = Get-EnvTestDefinition -CultureName es-ES
    

Description  
\---\---\-----  
Retrieve all tests with localized properties returned in Spanish.

### 示例 3

    $monitorConfigServiceRegistrationDefinition = Get-EnvTestDefinition -TestId Monitor_RegisteredWithConfigurationService
    

Description  
\---\---\-----  
Retrieve the definition of the 'Monitor_RegisteredWithConfigurationService' test.