# about_AcctADIdentitySnapIn

## TOPIC

    about_AcctADIdentitySnapin
    

## 简短说明

    Active Directory Identity Service PowerShell 管理单元为 Active Directory Identity Service 提供管理功能。
    

## 命令前缀

    此管理单元中的所有命令都有加了前缀“Acct”的名词。
    

## 详细说明

    通过 Active Directory Identity Service PowerShell 管理单元可以对 Active Directory Identity Service 进行本地管理和远程管理。  它提供了工具用于存储有关 Machine Creation Service 可以使用的 Active Directory 计算机帐户的详细信息。
    
    管理单元提供两个主要实体︰ 
    
    标识
    表示 Active Directory 计算机帐户，反映在 Machine Creation Service 上下文中帐户的状态。  Active Directory Identity Service 创建帐户或帐户导入 Active Directory Identity Service 时，会存储帐户密码。  一旦 Machine Creation Service 使用了帐户，密码将被丢弃。  对于向 Active Directory Identity Service 注册的帐户，标识具有以下附加状态信息。
    
        Available
            向服务注册了 Active Directory 帐户，知道帐户的密码，且该帐户可供另一个服务使用。  对于使用 New-AcctADAccount 命令成功创建的帐户或使用 Add-ADAccount 命令导入的帐户，最初分配这种状态。
    
        InUse
            已注册 Active Directory 帐户，且另一个服务已使用该帐户。  服务不再知道该帐户的密码。
    
        Error
            已注册 Active Directory 帐户，但在 Active Directory 中缺少、已禁用或已锁定该帐户。  不是使用 New-AcctADAccount 命令成功创建的帐户及不是使用 Add-ADAccount 命令导入的帐户处于这种状态。  可使用 Update-AcctADAccount 和 Repair-AcctADAccount 命令来解决处于这种状态的帐户的问题。
    
        Tainted
            已注册 Active Directory 帐户，所有使用服务已释放该帐户，但该帐户无法转为可用，因为不再知道其密码。  可使用 Repair-AcctADAccount 命令来重置帐户密码，并将帐户状态恢复为“Available”。
    
        标识还可以由 Machine Creation Service 标记为“Locked”以表明它们正在使用中，不得更改。
        这些服务还负责在 Active Directory 帐户不再需要独占访问时对其解锁。  可使用 Unlock-AcctADAccount 命令允许覆盖锁定（如有必要）。
    
    标识池
        可以配置创建新 Active Directory 帐户所需的所有信息的标识的容器。
        也可以通过导入 Active Directory 中已有的帐户来填充标识池。  向 Active Directory Identity Service 注册的所有帐户都必须放置到其中一个容器。  标识可以属于多个标识池，但在每个池中标识状态不能不同。  例如，正在使用中的标识将在其所属的所有标识池中标记为“InUse”。
    
        为了避免发生冲突的更改，在修改池内容的操作过程中，标识池还可以标记为“Locked”。  这些操作也负责解锁标识池。  可使用 unlock-AcctIdentityPool 命令允许覆盖锁定（如有必要）。
    

## ACTIVE DIRECTORY 权限

    创建帐户（使用 New-AcctADAccount 命令）
        要使用 PowerShell 创建新 Active Directory 帐户，必须使用在所需的 Active Directory 容器（由标识池组织单位参数指定）中具有足够权限的帐户来执行运行空间，才能创建帐户。
    
    导入帐户（使用 Add-AcctADAccount 命令） 
        此操作有两种模式︰知道 Active Directory 帐户密码的情况和不知道密码的情况。
    
        如果知道帐户密码，不需要 Active Directory 中的管理权限即可导入帐户。
        导入帐户后，提供的密码用于更改现有密码。
    
        如果不知道密码，则必须使用具有重置帐户密码权限的帐户执行运行空间。