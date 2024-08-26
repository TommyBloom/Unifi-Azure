# Unifi Network Application on Azure (ARM64)

This repository contains Azure Resource Manager (ARM) templates to deploy the Unifi Network Application container on Azure using ARM64 architecture.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FTommyBloom%2FUnifi-Azure%2Fmain%2Fazuredeploy.json)
[![Visualize](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.svg?sanitize=true)](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FTommyBloom%2FUnifi-Azure%2Fmain%2Fazuredeploy.json)

## Prerequisites

Before deploying this template, ensure you have the following:

1. An active Azure subscription
2. Permissions to create resources in Azure
3. A MongoDB instance (can be in Azure or elsewhere) accessible from Azure
4. A storage account and file share in Azure for persistent storage

## Deployment Process

1. Click the "Deploy to Azure" button above.
2. You'll be redirected to the Azure portal. If not already signed in, sign in to your Azure account.
3. Fill in the required parameters:
   - `containerGroupName`: Name for the container group (default: unifi-network-application)
   - `mongoHost`: Your MongoDB host address
   - `mongoUser`: MongoDB username (default: unifi)
   - `mongoPassword`: MongoDB password
   - `mongoDbName`: MongoDB database name (default: unifi)
   - `storageAccountName`: Name of your Azure storage account for persistent storage
   - `fileShareName`: Name of the file share in your storage account (default: unifi-config)
4. Select or create a new resource group.
5. Choose a region for deployment.
6. Review and accept the terms and conditions.
7. Click "Create" to start the deployment.

## Post-Deployment

After successful deployment:

1. The Unifi Network Application will be accessible via HTTPS on port 8443.
2. Use the DNS name or IP address provided in the deployment outputs to access the application.
3. Follow the Unifi Network Application setup wizard to complete the initial configuration.

## Architecture

This deployment uses:

- Azure Container Instances (ACI) to run the Unifi Network Application container
- Azure Storage Account with a File Share for persistent storage
- Your existing MongoDB instance for the database

The container is configured with:

- 2 CPU cores
- 4 GB of memory
- Public IP address
- DNS name label for easy access

Exposed ports:

- 8443 (HTTPS web interface)
- 3478 (STUN)
- 10001 (Device discovery)
- 8080 (Device communication)
- 1900, 8843, 8880, 6789, 5514 (various Unifi services)

## Customization

You can modify the `azuredeploy.json` template to adjust resources, add additional configurations, or change default values.

## Troubleshooting

If you encounter issues:

1. Check the container logs in the Azure portal
2. Ensure your MongoDB instance is accessible from Azure
3. Verify that the storage account and file share are correctly configured

## Security Considerations

- The template uses secure parameters for sensitive information like database passwords
- Ensure your MongoDB instance is properly secured
- Consider using Azure Private Link for more secure database connections
- Review and adjust network security group rules as needed

## Costs

This deployment will incur costs in your Azure subscription. Main cost components:

- Azure Container Instances
- Azure Storage Account
- Network egress

Monitor your usage and costs in the Azure portal.

## Support

For issues with the ARM template or deployment process, please open an issue in this GitHub repository.

For issues with the Unifi Network Application itself, please refer to the [official Ubiquiti support resources](https://help.ui.com/).

## Contributing

Contributions to improve the ARM templates or documentation are welcome. Please submit a pull request with your proposed changes.

## License

[Specify your license here]
