## XenApp 和 XenDesktop SDK<span id="par_richtext" class="anchor"></span>XenApp 和 XenDesktop 提供基于多个 Microsoft Windows PowerShell 3.0 版管理单元的 SDK，它允许您执行通过 Citrix Studio 控制台可以完成的任务，以及一些只使用 Studio 无法完成的任务。

自 7.5 版开始，XenApp 和 XenDesktop 共用统一的体系结构和管理：FlexCast Management Architecture。 这意味着 XenApp 提供了许多之前仅在 XenDesktop 中提供的功能；因此，与常用功能相关的 SDK 元素同样适用于 XenApp 和 XenDesktop，即使命令本身仅是指 XenDesktop 也是如此。

### XenDesktop 5 与 XenDesktop 7 SDK 之间的主要区别

- **全新的高级 SDK** — XenDesktop 7 提供了全新的高级 SDK，让您可以编写脚本、自动化站点创建以及轻松地进行快速维护。 高级 SDK 为您免除了很多低级 SDK 的复杂性，例如，您只需运行两个 cmdlet 即可创建一个新站点。

- **全新的低级 SDK** — 为全新的 XenDesktop 7 服务提供了单独的低级 SDK，包括为 Delegated Administration Service (DAS) 提供了增强的专用 SDK，此 SDK 之前在 XenDesktop 5 中是 Broker SDK 的一部分。 此外，还提供了用于 Monitor Service、环境测试以及配置日志记录等新功能的 SDK。

- **Windows 服务器操作系统计算机目录和交付组** — 可以使用 XenDesktop 7 SDK 交付托管在服务器操作系统上的经济高效的应用程序和桌面。

- **桌面操作系统计算机应用程序** — 桌面操作系统计算机应用程序在 SDK 级别发生了显著变化。 如果您有用于在桌面操作系统上运行应用程序的现有脚本，必须为 XenDesktop 7 更新这些脚本，因为几乎不进行向后兼容。

- **将设置应用于交付组中的计算机** — 在 XenDesktop 7 中，使用配置插槽，可以将设置应用于特定交付组中的计算机，而非站点中的所有计算机。 这样，就可以配置应用于给定交付组的设置。 系统提供了多个包含不同类型设置的预定义配置插槽，例如，用于 Receiver 或 App-V 发布服务器位置的 StoreFront 地址设置。 可以将插槽的一组设置仅应用于某个特定交付组，同时将同一插槽的另一组设置应用于另一个交付组。 可以使用与特定部署相对应的名称；例如，“销售部门策略”。

- **取代了目录类型** — 在 XenDesktop 7 中，已使用具有单个属性的目录取代了目录类型。 但是，为了向后兼容，仍然可以使用采用目录类型的现有脚本，例如，单一映像（池）和精简克隆（专用）等等，但是在内部这些目录类型会被转换为属性集。

!!! warning "警告" 在可行的情况下，维护了与 XenDesktop 5 目录类型的向后兼容。 但是，编写新脚本时，请勿使用目录类型；而是使用单个属性指定目录。

- **取代了桌面对象** — 在 XenDesktop 5 中，桌面对象是 Broker SDK 脚本中使用的 SDK 对象的主要类型之一。 桌面对象同时描述了计算机和计算机上的会话。 在 XenDesktop 7 中，此对象已被会话对象和计算机对象所取代，这两个对象均已扩展到可以执行桌面对象的工作。 但是，为了向后兼容，仍然可以使用采用了桌面对象的现有脚本。

!!! warning "警告" 在可行的情况下，维护了与 XenDesktop 5 的向后兼容。 但是，编写新脚本时，请勿使用桌面对象；而是指定会话对象和计算机对象。

### 策略规则方面的区别

SDK 与 Studio 控制台在策略规则方面存在区别。 在 SDK 中，授权和分配策略规则是独立的实体；但在控制台中，这些实体不可见，因为它们与交付组无缝合并在一起。 此外，SDK 中访问策略规则的限制性更低。

### 使用 SDK

SDK 由多个 PowerShell 管理单元组成，在安装 Controller 或 Studio 组件时，安装向导会自动安装这些管理单元。

访问并运行 cmdlet：

1. 在 PowerShell 3.0 中启动 shell。

> 要从控制台启动 shell，请单击 **Studio**，选择“PowerShell”选项卡，然后单击**启动 PowerShell**。
> 
> 必须使用拥有 Citrix 管理员权限的身份运行 shell 或脚本。 尽管在 Controller 上，本地管理员组的成员自动拥有完全管理权限以允许安装 XenDesktop，但 Citrix 建议，对于常规操作，应创建拥有相应权限的 Citrix 管理员，而不要使用本地管理员帐户。 如果运行的是 Windows Server 2008，必须以 Citrix 管理员身份运行 shell 或脚本，而不是以本地管理员组成员身份。

2. 要在脚本内使用 SDK cmdlet，应在 PowerShell 中设置执行策略。

> 有关 PowerShell 执行策略的详细信息，请参阅 Microsoft 文档。

3. 在 Windows PowerShell 控制台中使用 **Add -PSSnapin** 命令将需要的管理单元添加到 PowerShell 环境中。 V1 和 V2 表示管理单元的版本（XenDesktop 5 管理单元为版本 1；XenDesktop 7 管理单元为版本 2）。 例如，键入：

> Add-PSSnapin Citrix.ADIdentity.Admin.V2
> 
> 要导入所有 cmdlet，请键入：
> 
> Add-PSSnapin Citrix.*.Admin.V*
> 
> 导入后，可以访问 cmdlet 及其关联帮助。

有关典型用例的示例，请参阅 [SDK 入门](./getting-started.md)。

!!! tip "注意" 有关 cmdlet 的所有帮助文本的完整列表，请参阅 [PowerShell cmdlet 帮助](http://docs.citrix.com/en-us/xenapp-and-xendesktop/7-6/cds-sdk-wrapper-rho/xad-commands.html)。

### Group Policy SDK 用法

Citrix Group Policy SDK 可用来显示并配置组策略设置和过滤器。 它使用 PowerShell 提供程序创建与计算机和用户的设置及过滤器相对应的虚拟驱动器。 提供程序以 New-PSDrive 扩展的形式显示。 要使用组策略 SDK，必须安装 Studio 或 XenApp 和 XenDesktop SDK。

**添加 Group Policy SDK**

1. 要添加 Group Policy SDK，请键入：

    Add-PSSnapin citrix.common.grouppolicy
    

<br />  
2. 要访问帮助，请键入：

    help New-PSDrive -path localgpo:/
    

**使用 Group Policy SDK**

1. 要创建虚拟驱动器并加载该驱动器及设置，请键入：

    New-PSDrive &lt;Standard Parameters&gt; \[-PSProvider\]
    CitrixGroupPolicy *-Controller* &lt;string&gt;
    

    **New-PSDrive &lt;Standard Parameters&gt; \[-PSProvider\]
    CitrixGroupPolicy ***-Controller*** &lt;string&gt;**
    

> 其中 *-Controller* 是站点中您要与之连接并从中加载设置的 Controller 的完全限定的域名。