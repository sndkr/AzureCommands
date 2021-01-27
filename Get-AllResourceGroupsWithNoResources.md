function Get-AZResourceGroupsWithNoResources 
{
  process 
  {
        $allResourceGroups = Get-AZResourceGroup | ForEach-Object { $_.ResourceGroupName }

        $resourceGroupsWithResources = Get-AzResource | Group-Object ResourceGroupName | ForEach-Object { $_.Name }

        $emptyResourceGroups = $allResourceGroups | Where-Object { $_ -NotIn $resourceGroupsWithResources } 

        return $emptyResourceGroups
    }
}
