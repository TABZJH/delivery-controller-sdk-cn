# Get-EnvTestSuiteDefinition

Gets one or more test suite definitions.

## 语法

    Get-EnvTestSuiteDefinition [-TestSuiteId <String[]>] [-CultureName <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a list of test suite definitions that are available from currently running components.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
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
| TestSuiteId  | The id of one or more test suites.                                                                                              | false | true (ByValue) |                                       |
| CultureName  | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US". | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                      | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.String

A test suite id.### System.String[] An array of test suite ids.

## 返回值

### Citrix.EnvTest.Sdk.EnvTestSuiteDefinition

The definition of a test suite

## 示例

### 示例 1

    $allTestSuiteDefinitions = Get-EnvTestSuiteDefinition
    

Description  
\---\---\-----  
Retrieve all test suites.

### 示例 2

    $allTestSuiteDefinitionsTranslatedIntoSpanish = Get-EnvTestSuiteDefinition -CultureName es-ES
    

Description  
\---\---\-----  
Retrieve all test suites with localized properties returned in Spanish.

### 示例 3

    $infrastructureSuiteDefinition = Get-EnvTestSuiteDefinition -TestSuiteId Infrastructure
    

Description  
\---\---\-----  
Retrieve the definition of the 'Infrastructure' test suite.