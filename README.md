# Find Microsoft Tenant ID

A PowerShell function to return the Tenant ID for any Microsoft tenant using public APIs.

## How to use
Copy and paste the function into your PowerShell Script.

```
Function Find-TenantID {
    
    [CmdletBinding()]
     param(
        [Parameter(Position=0,mandatory=$true)]
        [string] $domain
    )

    try {
        $response = Invoke-RestMethod -UseBasicParsing -Uri "https://odc.officeapps.live.com/odc/v2.1/federationprovider?domain=$domain"
    }
    Catch {
        Return "Unable to run request"
    }

    #Return
    $response.tenantid

}
```

Run the following command:

```
Find-TenantID -domain ourcloudnetwork.com
```
