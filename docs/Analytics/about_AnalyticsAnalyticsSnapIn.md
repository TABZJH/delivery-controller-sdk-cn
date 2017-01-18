# about_AnalyticsAnalyticsSnapIn

## TOPIC

    about_AnalyticsAnalyticsSnapin 
    

## 简短说明

Analytics PowerShell 管理单元为 Analytics Service 提供管理功能。

## 命令前缀

    此管理单元中的所有命令都有加了前缀“Analytics”的名词。 
    

## 详细说明

    通过 Analytics Service PowerShell 管理单元可以对 Analytics Service 进行本地管理和远程管理。 
    
    Analytics Service 收集有关 DDC 的 Citrix CEIP 数据。 有关 CEIP 的详细信息，请参阅 http://more.citrix.com/XD-CEIP。 
    
    此管理单元中提供一些命令，由 Citrix 管理员用于启用数据收集、导入收集数据点文件以及查询 Analytics 数据库配置和服务的当前状态分析。 
    
    有关 Analytics Service 的详细信息，请参阅有关 Analytics Service 的帮助主题。 
    
    可使用命令“Get-Command -Module Citrix.Analytics.Admin.V1”查看此管理单元支持的命令完整列表。 
    
    有关每个命令的用法，可使用 Get-Help 命令来显示每个命令的帮助文本。 
    
    除了 Analytics Service 中硬编码的预先编程计划之外，管理员还可以使用 Set-AnalyticsSite 命令触发实时数据收集和上载。 可以指定注册表字符串值 HKLM/Software/Citrix/XDServices/Analytics/DoOperation 来指示执行 Set-AnalyticsSite 命令时要执行的收集类型。 如果此注册表值中存储的数据设置为“Collect”，在发出命令“Set-AnalyticsSite -Enabled $true”后，Analytics Service 立即开始收集。 收集的结果是一个 .zip 文件，其位置存储在注册表值“DoOperationResult”中。 收集的结果不会上载到 Citrix CEIP 站点。 
    
    如果“DoOperation”的值是“CollectAndUpload”，则执行收集，且结果还上载到 Citrix CEIP 站点。 
    
    如果“DoOperation”的值是“CollectSite”，则只收集站点数据。 有关站点数据的详细列表，请参阅 DataPoints.xml 文件中每个数据点的“Scope”参数，该文件位于 c:\Program Files\Citrix\XenDesktopPoshSDK\Module\ Citrix.XenDesktop.Admin.V1\Citrix.XenDesktop.Admin 中。
    
    如果“DoOperation”的值是“CollectHost”，则只收集主机数据，如数据点文件中指定。 
    
    可以使用 Import-AnalyticsDataDefinition 文件导入数据点文件。 该文件必须是 Citrix 签署的文件。 
    
    运行时，Analytics Service 定期使用 DDC 数据库中存储的最新数据点文件收集数据。 大约每 30 分钟执行一次数据收集。 每次收集运行 5 到 10 分钟，具体取决于要收集的数据大小。 服务已经过优化，以使用最少的系统资源来进行数据收集。 
    
    如果收集结果未立即上载，可以手动上载。 如果未手动上载，Analytics Service 将定期打包并上载。 
    如果由于任何原因导致上载失败，Service 将重试，但不会是在最近两次成功上载之间两倍时间量之前。 如果上载仍失败，之后 Service 将等待很长时间再去尝试下一次上载。 时间可以是几周或几个月。 
    系统重新启动会重置上载等待时间。 
    
    收集和上载算法和计划已在 Service 中硬编码，不能更改。