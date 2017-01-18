# Export-ConfigFeatureTable

Returns the current feature table.

## 语法

    Export-ConfigFeatureTable [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

## 相关命令

- [Set-ConfigSite](Set-ConfigSite.html)
- [Import-ConfigFeatureTable](Import-ConfigFeatureTable.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.String

## 示例

### 示例 1

    C:\PS> Export-ConfigFeatureTable
    <?xml version="1.0" encoding="utf-8">
    <Products xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="FeatureTable.xsd">
      <Product Code="XDT" Name="XenDesktop">
        <Editions>
          <Edition>PLT</Edition>
          <Edition>ENT</Edition>
          <Edition>APP</Edition>
          <Edition>STD</Edition>
        </Editions>
        <DefaultEdition>PLT</DefaultEdition>
        <VersionToBurninDates>
          <VersionToBurninDate Version="7.0" BurninDate="2013.0522" />
        </VersionToBurninDates>
        <LicensingModels>
          <LicensingModel>Concurrent</LicensingModel>
          <LicensingModel>UserDevice</LicensingModel>
        </LicensingModels>
        <DefaultLicensingModel>UserDevice</DefaultLicensingModel>
        <Features>
          <Feature Name="CustomRole">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="ConfigurationLogging">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="SingleUserMode">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="MultiSessionDesktops">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="SingleSessionDesktops">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="STD" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="MultiSessionApplications">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="SingleSessionApplications">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="APP" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="HistoricalMonitorData">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="CloudHostedMachines">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="HdxInsightIntegration">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="RemotePC">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
        </Features>
      </Product>
      <Product Code="MPS" Name="XenApp">
        <Editions>
          <Edition>PLT</Edition>
          <Edition>ENT</Edition>
        </Editions>
        <DefaultEdition>PLT</DefaultEdition>
        <VersionToBurninDates>
          <VersionToBurninDate Version="7.0" BurninDate="2013.0522" />
        </VersionToBurninDates>
        <LicensingModels>
          <LicensingModel>Concurrent</LicensingModel>
        </LicensingModels>
        <DefaultLicensingModel>Concurrent</DefaultLicensingModel>
        <Features>
          <Feature Name="CustomRole">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="ConfigurationLogging">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="SingleUserMode">
          </Feature>
          <Feature Name="MultiSessionDesktops">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="SingleSessionDesktops">
          </Feature>
          <Feature Name="MultiSessionApplications">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="SingleSessionApplications">
            <BurninDate ForProductEdition="PLT" MustBe="AtLeast">2013.0522</BurninDate>
            <BurninDate ForProductEdition="ENT" MustBe="AtLeast">2013.0522</BurninDate>
          </Feature>
          <Feature Name="HistoricalMonitorData">
          </Feature>
          <Feature Name="CloudHostedMachines">
          </Feature>
          <Feature Name="HdxInsightIntegration">
          </Feature>
          <Feature Name="RemotePC">
          </Feature>
        </Features>
      </Product>
    </Products>
    

Description  
\---\---\-----  
Returns the current feature table.