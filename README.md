# Hotel Ballroom Booking Website

A modern, responsive website for booking luxury hotel ballrooms.

## Deployment to Azure

This website is configured for deployment to Azure Static Web Apps. Here are the steps to deploy:

1. **Prerequisites**
   - An Azure account
   - Azure CLI installed
   - GitHub account

2. **Deployment Steps**

   a. **Create Azure Static Web App**
   ```bash
   # Login to Azure
   az login

   # Create a resource group (if you don't have one)
   az group create --name <resource-group-name> --location <location>

   # Create Static Web App
   az staticwebapp create \
     --name <app-name> \
     --resource-group <resource-group-name> \
     --location <location> \
     --source <your-github-repo-url> \
     --branch main \
     --app-location "/" \
     --output-location ""
   ```

   b. **Get the deployment token**
   ```bash
   az staticwebapp secrets list --name <app-name> --resource-group <resource-group-name>
   ```

   c. **Add the token to GitHub Secrets**
   - Go to your GitHub repository
   - Navigate to Settings > Secrets and variables > Actions
   - Add a new secret named `AZURE_STATIC_WEB_APPS_API_TOKEN`
   - Paste the deployment token as the value

3. **Verify Deployment**
   - After adding the secret, GitHub Actions will automatically deploy your site
   - You can monitor the deployment in the Actions tab of your repository
   - Once complete, your site will be available at `https://<app-name>.azurewebsites.net`

## Local Development

To run the site locally:

1. Clone the repository
2. Open `index.html` in your browser
3. Or use a local server:
   ```bash
   # Using Python
   python -m http.server 8000
   
   # Using Node.js
   npx serve
   ```

## Features

- Responsive design
- Modern UI/UX
- Ballroom listing and details
- Booking system
- API integration 