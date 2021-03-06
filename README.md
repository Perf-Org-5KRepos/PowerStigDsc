# PowerStigDsc (ARCHIVED)

**PowerStigDsc HAS MOVED** This project has been migrated into [PowerStig](https://github.com/Microsoft/PowerStig) and is currently archived.

|Branch|Status|
| ---- | ---- |
| master | [![Build status](https://ci.appveyor.com/api/projects/status/h9lcjalgdlneyd46/branch/master?svg=true)](https://ci.appveyor.com/api/projects/status/h9lcjalgdlneyd46/branch/master?svg=true) |

**PowerStigDsc** is a Windows PowerShell Desired State Configuration (DSC) composite resource to manage the configurable items of the DISA STIG's.
This is accomplished by using OSS DSC Resources that are specialized to a specific area of the STIG from the PowerShell gallery. PowerStigDsc depends on an external module [PowerStig](https://github.com/Microsoft/PowerStig) for the STIG data and multiple DSC resources to apply the setting. All of the required dependencies are defined in the module manifest so they are automatically downloaded if you install PowerStigDsc from the [PowerShell Gallery](https://www.powershellgallery.com/packages/PowerStigDsc).

This project has adopted the [Microsoft Open Source Code of Conduct](
  https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](
  https://opensource.microsoft.com/codeofconduct/faq/)
or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions
or comments.

## Contributing

Please check out common DSC Resources [contributing guidelines](
  https://github.com/PowerShell/DscResources/blob/master/CONTRIBUTING.md).

### Contributors

Thank you to everyone that has reviewed the project and provided feedback through issues.
We are especially thankful for those who have contributed pull requests to the code and documentation.

* [@athaynes](https://github.com/athaynes) (Adam Haynes)
* [@bgouldman](https://github.com/bgouldman) (Brian Gouldman)
* [@camusicjunkie](https://github.com/camusicjunkie)
* [@chasewilson](https://github.com/chasewilson) (Chase Wilson)
* [@jcwalker](https://github.com/jcwalker) (Jason Walker)
* [@mcollera](https://github.com/mcollera)
* [@regedit32](https://github.com/regedit32) (Reggie Gibson)

## Composite Resources

* [Browser](#Browser): Provides a mechanism to manage Browser STIG settings.

* [SqlServer](#SqlServer): Provides a mechanism to manage SqlServer STIG settings.

* [WindowsDnsServer](#WindowsDnsServer): Provides a mechanism to manage Windows DNS Server STIG settings.

* [WindowsFirewall](#WindowsFirewall): Provides a mechanism to manage the Windows Firewall STIG settings.

* [WindowsServer](#WindowsServer): Provides a mechanism to manage the Windows Server STIG settings.

### Browser

Provides a mechanism to manage Browser STIG settings.

#### Requirements

None

#### Parameters

* **[String] BrowserName _(Mandatory)_**: The version of the Browser that the configuration is applying to.
* **[String] BrowserVersion _(Optional)_**: The Browser version of the STIG you want to apply. If no value is provided, the most recent version of the STIG is applied.
* **[Hashtable] Exception _(Optional)_**: A hash table of the exceptions that should be applied to the server. The hashtable must be in the format StigId = Exception.
* **[Xml] OrgSetting _(Optional)_**: An XML document that contains the values for settings that contain a range of possible values.

#### Examples

* [Apply the Browser STIG to a node](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_Browser.ps1)

### SqlServer

Provides a mechanism to manage SqlServer STIG settings.

### Requirements

None

### Parameters

* **[String] SqlVersion _(Mandatory)_**: The version of SQL being used.
* **[String] SqlRole _(Mandatory)_**: The scope of SQL that the STIG covers. E.g. Instance, Database.
* **[Version] StigVersion _(Optional)_**: The version of the STIG you want to apply. If no value is provided, the most recent version of the STIG is applied.
* **[String] ServerInstance _(Mandatory)_**: The name of the SQL Instance that the STIG data will be applied to.
* **[String] Database _(Optional)_**: The Name of the database that the STIG will be applied to.
* **[Hashtable] Exception _(Optional)_**: A hash table of the exceptions to be applied to the server. The hashtable must be in the format StigId = Exception.
* **[Xml] OrgSetting _(Optional)_**: This is an XML file that overrides the default settings of allowable ranges in the STIG.
* **[PSObject] SkipRule _(Optional)_**: Rule Id/s that you do not want to be applied to the server.
* **[PSObject] SkipRuleType _(Optional)_**: Rule type/s that you do not want to be applied to the server.

#### Examples

* [Apply the Windows SQL Server STIG to a node](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_SqlServer_Default.ps1)
* [Apply the Windows SQL Server STIG to a node, but override the value of V-V-40942](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_SqlServer_Exception.ps1)
* [Apply the Windows SQL Server STIG to a node, but skip V-V-40942](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_SqlServer_SkipRule.ps1)
* [Apply the Windows SQL Server STIG to a node, but skip SqlScriptQueryRule](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_SqlServer_SkipRuleType.ps1)

### WindowsDnsServer

Provides a mechanism to manage Windows Dns Server STIG settings.

#### Requirements

None

#### Parameters

* **[String] OsVersion _(Mandatory)_**: The version of the server OS that the configuration is applying to.
* **[String] StigVersion _(Optional)_**: The version of the STIG you want to apply. If no value is provided, the most recent version of the STIG is applied.
* **[String] ForestName _(Optional)_**: The FQDN of the forest the configuration is being applied to. If a domain name is not applied, the domain of the computer used to generate the configuration is used.
* **[String] DomainName _(Optional)_**: The FQDN of the domain the configuration is being applied to. If a domain name is not applied, the domain of the computer used to generate the configuration is used.
* **[Hashtable] Exception _(Optional)_**: A hash table of the exceptions to be applied to the server. The hashtable must be in the format StigId = Exception.
* **[Xml] OrgSetting _(Optional)_**: This is an XML file that overrides the default settings of allowable ranges in the STIG.
* **[PSObject] SkipRule _(Optional)_**: Rule Id/s that you do not want to be applied to the server.
* **[PSObject] SkipRuleType _(Optional)_**: Rule type/s that you do not want to be applied to the server.

#### Examples

* [Apply the Windows DNS Server STIG to a node](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsDnsServer_Default.ps1)
* [Apply the Windows DNS Server STIG to a node, but override the value of V-1000](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsDnsServer_Exception.ps1)
* [Apply the Windows DNS Server STIG to a node, but skip the V-1000 setting](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsDnsServer_SkipRule.ps1)
* [Apply the Windows DNS Server STIG to a node, but skip the AuditPolicyRules](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsDnsServer_SkipRuleType.ps1)

### WindowsFirewall

Provides a mechanism to manage the Windows Firewall STIG settings.

#### Requirements

None

#### Parameters

* **[String] StigVersion _(Optional)_**: The version of the STIG you want to apply. If no value is provided, the most recent version of the STIG is applied.
* **[Hashtable] Exception _(Optional)_**: A hash table of the exceptions to be applied to the server. The hashtable must be in the format StigId = Exception.
* **[Xml] OrgSetting _(Optional)_**: This is an XML file that overrides the default settings of allowable ranges in the STIG.
* **[PSObject] SkipRule _(Optional)_**: Rule Id/s that you do not want to be applied to the server.
* **[PSObject] SkipRuleType _(Optional)_**: Rule type/s that you do not want to be applied to the server.

#### Examples

* [Apply the Windows Firewall STIG to a node](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsFirewall_Default.ps1)
* [Apply the Windows Firewall STIG to a node, but override the value of V-1000](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsFirewall_Exception.ps1)
* [Apply the Windows Firewall STIG to a node, but skip the V-1000 setting](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsFirewall_SkipRule.ps1)
* [Apply the Windows Firewall STIG to a node, but skip the AuditPolicyRules](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsFirewall_SkipRuleType.ps1)

### WindowsServer

Provides a mechanism to manage the Windows Server STIG settings.

#### Requirements

None

#### Parameters

* **[String] OsVersion _(Mandatory)_**: The version of the server OS that the configuration is applying to.
* **[String] OsRole _(Mandatory)_**: The role of the computer the configuration applies to.
* **[String] StigVersion _(Optional)_**: The version of the STIG you want to apply. If no value is provided, the most recent version of the STIG is applied.
* **[String] ForestName _(Optional)_**: The FQDN of the forest the configuration is being applied to. If a domain name is not applied, the domain of the computer used to generate the configuration is used.
* **[String] DomainName _(Optional)_**: The FQDN of the domain the configuration is being applied to. If a domain name is not applied, the domain of the computer used to generate the configuration is used.
* **[Hashtable] Exception _(Optional)_**: A hash table of the exceptions to be applied to the server. The hashtable must be in the format StigId = Exception.
* **[Xml] OrgSetting _(Optional)_**: This is an XML file that overrides the default settings of allowable ranges in the STIG.
* **[PSObject] SkipRule _(Optional)_**: Rule Id/s that you do not want to be applied to the server.
* **[PSObject] SkipRuleType _(Optional)_**: Rule type/s that you do not want to be applied to the server.

#### Examples

* [Apply the latest Windows Server STIG to a node](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsServer_Default.ps1)
* [Apply a specific Windows Server STIG version to a node](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsServer_StigVersion.ps1)
* [Apply the Windows Server STIG to a node, but override the default organizational settings with a local file](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsServer_OrgSettings.ps1)
* [Apply the Windows Server STIG to a node, but override the value of V-1000](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsServer_Exception.ps1)
* [Apply the Windows Server STIG to a node, but skip the V-1000 setting](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsServer_SkipRule.ps1)
* [Apply the Windows Server STIG to a node, but skip the AuditPolicyRules](
  https://github.com/Microsoft/PowerStigDsc/blob/master/Examples/Sample_WindowsServer_SkipRuleType.ps1)

## Versions

### 1.1.0.0

* Added ModuleVersion parameter to each Import-DscResource for all composite resources
* Added support for Technology enumeration added to PowerStig 1.1.0.0

### 1.0.0.0

* Browser Composite
* Windows DNS Server Composite
* Windows Firewall Composite
* Windows Server Composite
