```PowerShell
function Get-AZResourceGroupsWithNoResources 
{
  process 
  {
        $allResourceGroups = Get-AzResourceGroup | Select-Object ResourceGroupName

        $resourceGroupsWithResources = Get-AzResource | Group-Object ResourceGroupName | Select-Object Name

        $emptyResourceGroups = $allResourceGroups | Where-Object { $_ -NotIn $resourceGroupsWithResources } 

        return $emptyResourceGroups
    }
}
```
