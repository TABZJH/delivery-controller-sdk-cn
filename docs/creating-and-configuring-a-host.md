## 创建和配置主机

以下示例介绍主机的创建和配置方法。

开始之前，请务必按照[入门指南](./getting-started.md)中详细介绍的步骤进行操作，该文档说明了如何使用 Studio 执行要编写脚本的操作（在本例中是创建主机）以及收集 Studio 为执行任务所做的 SDK 操作的日志。 之后，可以自定义此输出，以生成用于自动完成主机创建的脚本。

!!! tip "注意" 为确保始终获得最新的增强功能和修复程序，Citrix 建议您按照本文档中所述的过程进行操作，而不是复制并粘贴示例脚本。 为了增强可读性，在脚本中添加了行号和换行符。

**了解脚本**

以下部分介绍由 Studio 生成的脚本各部分的作用。这将有助于您自定义自己的脚本。为了增强可读性，添加了行号。

```powershell
1. Get-LogSite -AdminAddress 'mycontroller.example.com:80'
```

查询配置日志记录服务，以检索有关站点配置的信息。

```powershell
2. Start-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80'
-Source 'Studio' -StartTime 14/08/2013 14:30:28 -Text 'Create Connection `'Example XenServer`''
```

通过配置日志记录操作启动高级别日志记录操作（其中将包含其余命令）。返回将提供给后续操作的日志 ID。

```powershell
3. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

设置将由配置 cmdlet 使用的主机服务的位置。 由于主机服务提供 PowerShell 提供程序，而且并非所有 cmdlet 都能取得服务的地址，所以此 cmdlet 将设置默认位置。

```powershell
4. New-Item -ConnectionType 'XenServer' -HypervisorAddress @('http://xenhost1.example.com') -LoggingId e355ce51-8cbb-400a-ae81-1fdc567239cb -Path @('XDHyp:\Connections\Example XenServer') -Scope @() -Password ******** -UserName 'root'
```

创建与 XenServer (xenhost1.example.com) 的连接。这并非持续型连接，仅可供此 PowerShell 运行空间使用。

```powershell
5. Stop-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -EndTime 14/08/2013 14:30:29 -HighLevelOperationId 'e355ce51-8cbb-400a-ae81-1fdc567239cb' -IsSuccessful $True
```

停止先前开始的记录操作，并指示操作成功。

```powershell
6. Get-LogSite -AdminAddress 'mycontroller.example.com:80'
```

查询配置日志记录服务，以检索有关站点配置的信息。

```powershell
7. Start-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -Source 'Studio' -StartTime 14/08/2013 14:30:30 -Text 'Update Connection `'Example XenServer`''
```

启动新的高级别日志记录操作。

```powershell
8. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

重新设置主机服务地址详细信息（请注意，下面优化的脚本中删除了此重复操作）。

```powershell
9. Set-Item -HypervisorAddress @('http://xenhost1.example.com','http://xenhost2.example.com') -LoggingId 44e15629-6906-4840-a36c-984aaf67be6d -PassThru -Path @('XDHyp:\\Connections\\Example XenServer') -Password ******** -UserName 'root'
```

更新第 4 步中创建的连接。由于池中存在多个 XenServer，因此它将提供所有地址来实现高可用性。

```powershell
10. Stop-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -EndTime 14/08/2013 14:30:31 -HighLevelOperationId '44e15629-6906-4840-a36c-984aaf67be6d' -IsSuccessful \$True
```

停止第 7 步中开始的日志记录操作。

```powershell
11. Get-LogSite -AdminAddress 'mycontroller.example.com:80'
```

查询配置日志记录服务，以检索有关站点配置的信息。

```powershell
12. Start-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -Source 'Studio'
-StartTime 14/08/2013 14:31:03 -Text 'Create Resources `'Example Resources`' and Persist Connection `'Example XenServer`''
```

开始执行新的日志记录操作。

```powershell
13. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

重新设置主机服务地址详细信息。

```powershell
14. Get-ChildItem -Path @('XDHyp:\Connections')
```

获取主机连接的内容以填充向导对话框。

```powershell
15. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

重新设置主机服务地址详细信息。

```powershell
16. Remove-Item -LoggingId 76caa3f4-df93-4cb2-b78d-6a8824766314 -Path @('XDHyp:\Connections\Example XenServer')
```

删除向导中创建的临时连接。

```powershell
17. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

重新设置主机服务地址详细信息。

```powershell
18. New-Item -ConnectionType 'XenServer' -HypervisorAddress @('http://xenhost1.example.com','http://xenhost2.example.com') -LoggingId 76caa3f4-df93-4cb2-b78d-6a8824766314 -Path @('XDHyp:\\Connections\\Example XenServer') -Persist -Scope @() -Password ******** -UserName 'root'
```

以持续型连接的形式重新创建连接，连接将写入数据库并可供其他 PowerShell 运行空间使用。

```powershell
19. New-BrokerHypervisorConnection -AdminAddress 'mycontroller.example.com:80' -HypHypervisorConnectionUid a14096ba-5074-44ff-b596-371e345c0449 -LoggingId 76caa3f4-df93-4cb2-b78d-6a8824766314
```

将主机连接添加到 Broker Service。

```powershell
20. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

重新设置主机服务地址详细信息。

```powershell
21. New-Item -HypervisorConnectionName 'Example XenServer' -LoggingId 76caa3f4-df93-4cb2-b78d-6a8824766314 -NetworkPath @('XDHyp:\Connections\Example XenServer\Network0.network') -Path @('XDHyp:\HostingUnits\Example Resources') -PersonalvDiskStoragePath @('XDHyp:\Connections\Example XenServer\PvdStorage.storage') -RootPath 'XDHyp:\Connections\Example XenServer' -StoragePath
@('XDHyp:\Connections\Example XenServer\Primary OS.storage')
```

使用第 14 步中收集的信息创建托管单元（在 Studio 中称为“资源”）。

```powershell
22. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'
```

重新设置主机服务地址详细信息。

```powershell
23. Get-Item -Path @('XDHyp:\Connections\Example XenServer')
```

检索新创建的对象。

```powershell
Stop-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -EndTime 14/08/2013 14:31:07 -HighLevelOperationId '76caa3f4-df93-4cb2-b78d-6a8824766314' -IsSuccessful $True
```

停止先前开始的记录操作，并指示操作成功。

**自定义脚本**

以下部分介绍如何将 Studio 输出转换并修改成更适用的脚本。 以下脚本经过简化，与上面的 Studio 脚本不同，在向导中收集信息期间，它不会创建临时主机连接，而是创建持续型连接。 之后，将从此连接内查询信息来创建托管单元（资源）。 请注意，LoggingId 和 HypHyperConnectionUid 详细信息不同。

为了增强可读性，添加了行号；每个编号项都是一个 PowerShell 命令。

```powershell
1. Start-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -Source 'Studio' -Text 'Create Connection \`'Example XenServer\`''

2. Set-HypAdminConnection -AdminAddress 'mycontroller.example.com:80'

3. New-Item -ConnectionType 'XenServer' -HypervisorAddress @('http://xenhost1.example.com','http://xenhost2.example.com')-LoggingId
76caa3f4-df93-4cb2-b78d-6a8824766314 -Path @('XDHyp:\\Connections\\Example XenServer') -Persist -Scope @() -Password \*\*\*\*\*\*\*\* -UserName 'root'

4. Get-ChildItem -Path @('XDHyp:\Connections')

5. New-BrokerHypervisorConnection -AdminAddress 'mycontroller.example.com:80' -HypHypervisorConnectionUid a14096ba-5074-44ff-b596-371e345c0449 -LoggingId
76caa3f4-df93-4cb2-b78d-6a8824766314

6. New-Item -HypervisorConnectionName 'Example XenServer' -LoggingId
76caa3f4-df93-4cb2-b78d-6a8824766314 -NetworkPath @('XDHyp:\Connections\Example XenServer\Network
0.network') -Path @('XDHyp:\HostingUnits\Example Resources') -PersonalvDiskStoragePath @('XDHyp:\Connections\Example XenServer\Pvd Storage.storage') -RootPath 'XDHyp:\Connections\Example XenServer' -StoragePath @('XDHyp:\Connections\Example XenServer\PrimaryOS.storage')

7. Stop-LogHighLevelOperation -AdminAddress 'mycontroller.example.com:80' -HighLevelOperationId '76caa3f4-df93-4cb2-b78d-6a8824766314 -IsSuccessful $True
```