# Start-EnvTestTask

Starts a new test task.

## 语法

    Start-EnvTestTask -TestId <String> [-TargetIdType <String>] [-TargetId <String>] [-CultureName <String>] [-IgnoreRelatedObjects] [-RunAsynchronously] [-ExcludeNotRunTests] [-AdminAddress <String>] [<CommonParameters>]
    
    Start-EnvTestTask -TestSuiteId <String> [-TargetIdType <String>] [-TargetId <String>] [-CultureName <String>] [-IgnoreRelatedObjects] [-RunAsynchronously] [-ExcludeNotRunTests] [-AdminAddress <String>] [<CommonParameters>]
    
    Start-EnvTestTask -InputObject <PSObject[]> [-CultureName <String>] [-IgnoreRelatedObjects] [-RunAsynchronously] [-ExcludeNotRunTests] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Starts a new test task based on a set of criteria provided via parameters or piped input and either waits for the tests to run or returns immediately depending on how it is called. When running a test suite and providing a target object for that suite, the service will discover related objects by default, but this behavior may be disabled if desired.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Get-EnvTestTask](Get-EnvTestTask.html)
- [New-EnvTestDiscoveryTargetDefinition](New-EnvTestDiscoveryTargetDefinition.html)
- [Switch-EnvTestTask](Switch-EnvTestTask.html)
- [Stop-EnvTestTask](Stop-EnvTestTask.html)
- [Remove-EnvTestTask](Remove-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称                   | 说明                                                                                                                                                                                                | 是否必需？ | 管道输入           | 默认值                                   |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| TestId               | Test identifiers. If specified, do not specify -TestSuiteId.                                                                                                                                      | true  | false          | 空                                     |
| TestSuiteId          | Test suite identifiers. If specified, do not specify -TestId.                                                                                                                                     | true  | false          | 空                                     |
| InputObject          | One or more test targets defining the task, see Input Types for details about what kind of objects are permissible. Any valid object passed to this parameter may also be piped into this cmdlet. | true  | true (ByValue) | 空                                     |
| TargetIdType         | Describes the type of corresponding object passed with -TargetId                                                                                                                                  | false | false          | 空                                     |
| TargetId             | The Ids that object tests or tests suites will target. By default, other components are queried for objects related to these.                                                                     | false | false          | 空                                     |
| CultureName          | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US".                                                                   | false | false          | The current user interface culture    |
| IgnoreRelatedObjects | Do not ask other components for objects related to a specified target.                                                                                                                            | false | false          | False                                 |
| RunAsynchronously    | Do not wait for the test run to complete, return immediately.                                                                                                                                     | false | false          | False                                 |
| ExcludeNotRunTests   | If set, tests that are not run because no object matching their requirements is found are NOT included in test counts and results.                                                                | false | false          | False (include Not Run tests)         |
| AdminAddress         | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                        | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.EnvTest.Sdk.EnvTestDiscoveryTargetDefinition

A single EnvTestDiscoveryTargetDefinition can be specified to target one test or test suite.### Citrix.EnvTest.Sdk.EnvTestDiscoveryTargetDefinition[] An array of EnvTestDiscoveryTargetDefinition(s) can be specified to target any combination of tests and/or test suites.### PSCustomObject A single PSCustomObject with properties matching the required EnvTestDiscoveryTargetDefinition properties can be specified to target one test or test suite.### PSCustomObject[] An array of PSCustomObject(s) with properties matching the required EnvTestDiscoveryTargetDefinition properties can be specified to target any combination of tests and/or test suites.

## 返回值

### Ctrix.EnvTest.Sdk.EnvTestTask

The newly started task.

## 示例

### 示例 1

    $singleSimpleTestTask = Start-EnvTestTask -TestId Monitor_RegisteredWithConfigurationService
    

Description  
\---\---\-----  
Create and start a task with a single test and no target object.

### 示例 2

    $singleSimpleTestTaskInSpanish = Start-EnvTestTask -TestId Monitor_RegisteredWithConfigurationService -CultureName es-ES
    

Description  
\---\---\-----  
Create and start a task with a single test and no target object, with localized properties translated into Spanish.

### 示例 3

    $singleSimpleTestSuiteTask = Start-EnvTestTask -TestSuiteId Infrastructure
    

Description  
\---\---\-----  
Create and start a task with a single test suite and no target object.

### 示例 4

    $singleTestSuiteTask = Start-EnvTestTask -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid
    

Description  
\---\---\-----  
Create and start a task with a single test suite and a catalog target object.

### EXAMPLE 5

    $singleTestSuiteTask = Start-EnvTestTask -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid -RunAsynchronously
    

Description  
\---\---\-----  
Create and start a task with a single test suite and a catalog target object, and return immediately not waiting for the tests to complete.

### EXAMPLE 6

    $adAccountPool = Get-AcctIdentityPool
              $singleTestTaskWithNoObjectDiscovery = StartEnvTestTask -IgnoreRelatedObjects -TestId ADIdentity_IdentityPool_ValidatePoolIsUnlocked -TargetIdType IdentityPool -TargetId $adAccountPool.IdentityPoolUid
    

Description  
\---\---\-----  
Create and start a task with a single test, a target object for that test, and no object discovery based on that target.

### EXAMPLE 7

    $singleSimpleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Infrastructure
              $singleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid
              $inputObjects = @($singleSimpleTestSuiteTaskTarget, $singleTestSuiteTaskTarget)
              Start-EnvTestTask -InputObject $inputObjects
    

Description  
\---\---\-----  
Create two different discovery target definitions, put them in an array, then start a task based on both via -InputObject.