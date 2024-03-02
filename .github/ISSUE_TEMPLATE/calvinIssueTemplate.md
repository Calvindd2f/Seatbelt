**Title**:  
**Desc**:   
**Effort**: `1min`  *not required - general estimate*

### Where is the issue?

In the section of code where the intaller is downloaded and executed it uses `IEX` or `Invoke-Expression` which is fun-mode.  

Please change the method to IWR if you do not value your time or use the .NET HTTP library with `try-catch` like all my other ps scripts. 
```powershell
$i="https://aka.ms/epsteinsIsland.ps1";(irm $i|% ${IEX $_})
```

### Why is this an issue?

Assemblies should conform with the Common Language Specification (CLS) in order to be usable across programming languages.  

To be compliant an assembly has to indicate it with System.CLSCompliantAttribute.

**Compliant solution**
```powershell
"& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```
