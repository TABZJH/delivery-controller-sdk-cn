# New-BrokerCatalog

Adds a new catalog to the site.

## 语法

    New-BrokerCatalog [-Name] <String> [-AllocationType] <AllocationType> [-CatalogKind] <CatalogKind> [-PvsForVM <String[]>] [-Description <String>] [-IsRemotePC <Boolean>] [-MachinesArePhysical <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-Scope <String[]>] [-TenantId <Guid>] [-UUID <Guid>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-BrokerCatalog [-Name] <String> [-AllocationType] <AllocationType> [-ProvisioningType] <ProvisioningType> [-SessionSupport] <SessionSupport> [-PersistUserChanges] <PersistUserChanges> [-ProvisioningSchemeId <Guid>] [-Description <String>] [-IsRemotePC <Boolean>] [-MachinesArePhysical <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-Scope <String[]>] [-TenantId <Guid>] [-UUID <Guid>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

New-BrokerCatalog adds a catalog through which machines can be provided to the site.

In order for a machine to register in a site, the machine must belong to a catalog with which it is compatible. The compatibility of a machine with a catalog is determined by two of the parameters of New-BrokerCatalog:

o MinimalFunctionalLevel: The minimal functional level supported in the catalog. The functional level of the machine is determined by the capabilities of the Citrix VDA software on it. o SessionSupport: The session support (single/multi) of the catalog. The session support of the machine is determined by the variant of the Citrix VDA software installed (workstation/terminal services, respectively).

## 相关命令

- [Get-BrokerCatalog](Get-BrokerCatalog.html)
- [Rename-BrokerCatalog](Rename-BrokerCatalog.html)
- [Remove-BrokerCatalog](Remove-BrokerCatalog.html)
- [Set-BrokerCatalog](Set-BrokerCatalog.html)

## 参数

<table>
  <tr>
    <th>
      名称
    </th>
    
    <th>
      说明
    </th>
    
    <th>
      是否必需？
    </th>
    
    <th>
      管道输入
    </th>
    
    <th>
      默认值
    </th>
  </tr>
  
  <tr>
    <td>
      名称
    </td>
    
    <td>
      Specifies a name for the catalog. Each catalog within a site must have a unique name.
    </td>
    
    <td>
      true
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      AllocationType
    </td>
    
    <td>
      Specifies how machines in the catalog are assigned to users. Values can be:<br />o Static - Machines in a catalog of this type are permanently assigned to a user.<br />o Permanent - equivalent to 'Static'.<br />o Random - Machines in a catalog of this type are picked at random and temporarily assigned to a user.
    </td>
    
    <td>
      true
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      CatalogKind
    </td>
    
    <td>
      Deprecated: The type of machines the catalog will contain. Values can be: ThinCloned, SingleImage, PowerManaged, Unmanaged, Pvs, Pvd or PvsPvd.<br />Thin-Cloned, Single-Image and Personal vDisk Catalogs<br />-----------------------------------------------------<br />Thin-cloned and single-image catalog kinds are for machines created and managed with Provisioning Services for VMs. All machines in this type of catalog are managed, and so must be associated with a hypervisor connection.<br />A thin-cloned catalog is used for original golden VM images that are cloned when they are assigned to a VM, and users' changes to the VM image are retained after the VM is restarted.<br />A single-image catalog is used when multiple machines provisioned with Provisioning Services for VMs all share a single golden VM image when they run and, when restarted, they revert to the original VM image state.<br />A personal vDisk catalog is similar to a single-image catalog, but it also uses personal vDisk technology.<br />PowerManaged<br />------------<br />This catalog kind is for managed machines that are manually provisioned by administrators. All machines in this type of catalog are managed, and so must be associated with a hypervisor connection.<br />Unmanaged<br />---------<br />This catalog kind is for unmanaged machines, so there is no associated hypervisor connection.<br />PVS<br />---<br />This catalog kind is for managed machines that are provisioned using Provisioning Services. All machines in this type of catalog are managed, and so must be associated with a hypervisor connection. Only shared desktops are suitable for this catalog kind.<br />A Provisioning Services-personal vDisk (PvsPvd) catalog is similar to a Provisioning Services catalog, but it also uses personal vDisk technology.
    </td>
    
    <td>
      true
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      ProvisioningType
    </td>
    
    <td>
      Specifies the ProvisioningType for the catalog. Values can be:<br />o Manual - No provisioning.<br />o PVS - Machine provisioned by PVS (machine may be physical, blade, VM,...).<br />o MCS - Machine provisioned by MCS (machine must be VM).
    </td>
    
    <td>
      true
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      SessionSupport
    </td>
    
    <td>
      Specifies whether machines in the catalog are single or multi-session capable. Values can be:<br />o SingleSession - Single-session only machine.<br />o MultiSession - Multi-session capable machine.
    </td>
    
    <td>
      true
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      PersistUserChanges
    </td>
    
    <td>
      Specifies how user changes are persisted on machines in the catalog. Possible values are:<br />o OnLocal: User changes are stored on the machine's local storage.<br />o Discard: User changes are discarded.<br />o OnPvd: User changes are stored on the user's personal vDisk.
    </td>
    
    <td>
      true
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      PvsForVM
    </td>
    
    <td>
      Deprecated:<br />Identifies the provisioning scheme used by this catalog. To be specified in the format: ProvisioningSchemeGuid:ServiceGroupGuid. Applicable only to thin-cloned, single-image or personal vDisk catalogs.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      说明
    </td>
    
    <td>
      A description for the catalog.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      IsRemotePC
    </td>
    
    <td>
      Specifies whether this is to be a Remote PC catalog.<br />IsRemotePC can only be enabled when:<br />o SessionSupport is SingleSession<br />o MachinesArePhysical is true.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
      false
    </td>
  </tr>
  
  <tr>
    <td>
      MachinesArePhysical
    </td>
    
    <td>
      Specifies whether machines in the catalog can be power-managed by the Citrix Broker Service. Where the Citrix Broker Service cannot control the power state of themachine specify $true, otherwise $false. Can only be specified together with a provisioning type of Pvs or Manual, or if used with the legacy CatalogKind parameter only with Pvs or PvsPvd catalog kinds.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      MinimumFunctionalLevel
    </td>
    
    <td>
      The minimum FunctionalLevel required for machines to register in the site.<br />Valid values are L5, L7, L7_6
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
      The FunctionalLevel of the current release (L7_6); by default no machines with less than the most current FunctionalLevel will be functional.
    </td>
  </tr>
  
  <tr>
    <td>
      PvsAddress
    </td>
    
    <td>
      Specifies the URL of the Provisioning Services server. Only applicable to Provisioning Services or Provisioning Services-personal vDisk catalogs.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      PvsDomain
    </td>
    
    <td>
      Specifies the Active Directory domain of the Provisioning Services server. Only applicable to Provisioning Services or Provisioning Services-personal vDisk catalogs.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      RemotePCHypervisorConnectionUid
    </td>
    
    <td>
      Specifies the hypervisor connection to use for powering on remote PCs in this catalog (only allowed when IsRemotePC is true).
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      作用域
    </td>
    
    <td>
      Specifies the name of the delegated administration scope to which the catalog belongs.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      TenantId
    </td>
    
    <td>
      Specifies identity of tenant associated with catalog. Must always be specified in multitenant sites, must not be specified otherwise.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      UUID
    </td>
    
    <td>
      An optional GUID for this catalog.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
      A new GUID is generated if none is supplied.
    </td>
  </tr>
  
  <tr>
    <td>
      ZoneUid
    </td>
    
    <td>
      Zone Uid associated with this catalog.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
      If no Uid is provided the catalog is associated with Primary Zone.
    </td>
  </tr>
  
  <tr>
    <td>
      LoggingId
    </td>
    
    <td>
      指定此 cmdlet 调用所属的高级操作的标识符。 Desktop Studio 和 Desktop Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td>
      AdminAddress
    </td>
    
    <td>
      Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address.
    </td>
    
    <td>
      false
    </td>
    
    <td>
      false
    </td>
    
    <td>
      Localhost. Once a value is provided by any cmdlet, this value will become the default.
    </td>
  </tr>
  
  <tr>
    <td>
      ProvisioningSchemeId
    </td>
    
    <td>
      Specifies the identity of the MCS provisioning scheme the new catalog is associated with (can only be specified for new catalogs with a ProvisioningType of MCS).
    </td>
    
    <td>
      false
    </td>
    
    <td>
      true (ByPropertyName)
    </td>
    
    <td>
      $null
    </td>
  </tr>
</table>

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Broker.Admin.SDK.Catalog

New-BrokerCatalog returns the created catalog.

## 示例

### 示例 1

    C:\PS> New-BrokerCatalog -AllocationType Static -CatalogKind Unmanaged -Description "Catalog1 Description" -Name "Catalog1 Name"
    

Description  
\---\---\-----  
This command creates a catalog that can contain unmanaged physical or virtual machines that are permanently assigned to the user.

### 示例 2

    C:\PS> New-BrokerCatalog -AllocationType Random -CatalogKind PowerManaged -Description "catalog 2 Description" -Name "Catalog2 Name"
    

Description  
\---\---\-----  
This command creates a catalog that can contain power-managed machines that are randomly assigned to the user.

### 示例 3

    C:\PS> New-BrokerCatalog -AllocationType Random -CatalogKind PVS -Description "PVS Catalog Desc" -Name "PVS Catalog Name" -PvsAddress "pvsServer@pvsDomain.com" -PvsDomain "pvsDomain.com" -PvsForVM $($farmGuid:$schemeGuid)
    

Description  
\---\---\-----  
This command creates a catalog that can contain managed machines that are provisioned using Provisioning Services.