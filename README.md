{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "serverFarmName": {
      "type": "string",
      "defaultValue": "DevOps_Team"
    },
    "serverFarmResourceGroup": {
      "type": "string",
      "defaultValue": "DevOps_Team"
    }},
  "variables": {
    "sample-web appName": "[concat('sample-web app', uniqueString(resourceGroup().id))]"},
  "resources": [
    {
      "name": "[variables('sample-web appName')]",
      "type": "Microsoft.Web/sites",
      "location": "centralus",
      "apiVersion": "2015-08-01",
      "dependsOn": [ ],
      "tags": {
        "[concat('hidden-related:', resourceId(parameters('serverFarmResourceGroup'), 'Microsoft.Web/serverFarms', parameters('serverFarmName')))]": "Resource",
        "displayName": "sample-web app"
      },
      "properties": {
        "name": "[variables('sample-web appName')]",
        "serverFarmId": "[resourceId(parameters('serverFarmResourceGroup'), 'Microsoft.Web/serverFarms', parameters('serverFarmName'))]"
      }
    }],
  "outputs": {}
}
