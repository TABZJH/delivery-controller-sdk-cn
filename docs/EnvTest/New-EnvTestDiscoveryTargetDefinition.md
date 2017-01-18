# New-EnvTestDiscoveryTargetDefinition

Creates a new EnvTestDiscoveryTargetDefinition object

## 语法

    New-EnvTestDiscoveryTargetDefinition -TestId <String> [-TargetIdType <String>] [-TargetId <String>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-EnvTestDiscoveryTargetDefinition -TestSuiteId <String> [-TargetIdType <String>] [-TargetId <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Creates a new EnvTestDiscoveryTargetDefinition object that can be piped into Start-EnvTestTask to define one or more targets of execution, optionally including root objects for discovery.

## 相关命令

- [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
- [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
- [Get-EnvTestTask](Get-EnvTestTask.html)
- [Start-EnvTestTask](Start-EnvTestTask.html)
- [Switch-EnvTestTask](Switch-EnvTestTask.html)
- [Stop-EnvTestTask](Stop-EnvTestTask.html)
- [Remove-EnvTestTask](Remove-EnvTestTask.html)
- [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
- [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)

## 参数

| 名称           | 说明                                                                                                                           | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| TestId       | Test identifiers. If specified, do not specify -TestSuiteId.                                                                 | true  | false | 空                                     |
| TestSuiteId  | Test suite identifiers. If specified, do not specify -TestId.                                                                | true  | false | 空                                     |
| TargetIdType | Describes the type of corresponding object passed with -TargetId                                                             | false | false | 空                                     |
| TargetId     | The Ids that object tests or test suites will target. By default, other components are queried for objects related to these. | false | false | 空                                     |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                   | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.EnvTest.Sdk.EnvTestDiscoveryTargetDefinition

Defines a target of a task

## 示例

### 示例 1

    $singleSimpleTestTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestId Monitor_RegisteredWithConfigurationService
    $singleSimpleTestTaskTarget | Start-EnvTestTask
    

Description  
\---\---\-----  
Create a discovery target definition with a single test and no target object, then start a task based on it.

### 示例 2

    $singleSimpleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Infrastructure
    $singleSimpleTestSuiteTaskTarget | Start-EnvTestTask
    

Description  
\---\---\-----  
Create a discovery target definition with a single test suite and no target object, then start a task based on it.

### 示例 3

    $singleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid
    $singleTestSuiteTaskTarget | Start-EnvTestTask
    

Description  
\---\---\-----  
Create a discovery target definition with a single test suite and a catalog target object, then start a task based on it.

### 示例 4

    $singleSimpleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Infrastructure
    $singleTestSuiteTaskTarget = New-EnvTestDiscoveryTargetDefinition -TestSuiteId Catalog -TargetIdType Catalog -TargetId $(Get-BrokerCatalog).Uuid
    @($singleSimpleTestSuiteTaskTarget, $singleTestSuiteTaskTarget) | Start-EnvTestTask
    

Description  
\---\---\-----  
Create two different discovery target definitions, put them in an array, then start a task based on both.