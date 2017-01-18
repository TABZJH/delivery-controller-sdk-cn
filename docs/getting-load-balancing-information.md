## 获取负载平衡信息

可以使用服务器操作系统计算机向多个用户交付托管在服务器操作系统上的经济高效的应用程序和桌面。

要平衡部署中服务器操作系统计算机的负载，可以使用 Citrix 策略。 多个负载平衡策略设置都可以用来在交付 Windows 服务器操作系统计算机的服务器之间启用和配置负载管理。 有关详细信息，请参阅负载管理策略设置参考文档。 可以通过 Studio 或 Windows 中的组策略管理控制台使用策略；有关详细信息，请参阅“策略”文档。

要查看负载，可以使用 Citrix Director 或 Studio 控制台或者 PowerShell SDK。以下示例显示了如何使用 PowerShell SDK 显示负载。

!!! tip "注意" 如果使用过早期版本的 XenDesktop，您可能很熟悉 **qfarm/load** 命令。 此工具不再可用，但可以使用 PowerShell 显示如以下示例所示的类似输出。

**示例：获取负载指数值**

要显示计算机列表、计算/测量的负载指数值以及计算机上运行的会话数，请执行以下操作：

  1. 在 PowerShell 中启动 shell。有关详细信息，请参阅 [XenApp 和 XenDesktop SDK](./)。

  2. 键入：

```powershell
Get-BrokerMachine -SessionSupport MultiSession -Property 'DnsName','LoadIndex','SessionCount'
```

**注意：**负载指数值最大可以是 10000。 负载指数值表示从已配置的源计算得出的 VDA 计算机负载，例如会话数量。 值 10000 表示 VDA 计算机满载；Broker 不再向该计算机发送其他用户会话。

有关详细信息和示例，请参阅 get-brokermachine cmdlet 的 cmdlet 帮助以及 about_broker_filtering-xd7.html 等“关于”主题。 请参阅︰ [PowerShell cmdlet 帮助](http://docs.citrix.com/en-us/xenapp-and-xendesktop/7-6/cds-sdk-wrapper-rho/xad-commands.html)。