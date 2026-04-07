# TodaysDemo

A sample ASP.NET Core 8 Razor Pages web application for demonstrating deployment to **Azure Web App** via **GitHub Actions**.

## Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8)
- An [Azure account](https://azure.microsoft.com/free/) with an Azure Web App created (Windows or Linux, .NET 8 runtime)
- A GitHub repository with this code

## Running Locally

```bash
dotnet restore
dotnet run
```

Navigate to `https://localhost:5001` (or the port shown in the terminal).

## Deploying to Azure via GitHub Actions

The workflow at [`.github/workflows/azure-webapps-deploy.yml`](.github/workflows/azure-webapps-deploy.yml) builds and deploys the app on every push to the `main` branch.

### Setup Steps

1. **Create an Azure Web App**
   - In the Azure Portal, create a new Web App with the **.NET 8** runtime stack.

2. **Get the Publish Profile**
   - In your Web App's Overview page, click **Download publish profile**.

3. **Add a GitHub Secret**
   - In your GitHub repository go to **Settings → Secrets and variables → Actions**.
   - Create a new secret named `AZURE_WEBAPP_PUBLISH_PROFILE` and paste the publish profile XML content.

4. **Set the App Name**
   - In `.github/workflows/azure-webapps-deploy.yml`, replace `your-azure-webapp-name` with your actual Azure Web App name:
     ```yaml
     AZURE_WEBAPP_NAME: your-azure-webapp-name
     ```

5. **Push to `main`**
   - Push your code to the `main` branch. The GitHub Actions workflow will automatically build and deploy the app to Azure.

## Project Structure

```
TodaysDemo.csproj       # Project file
Program.cs              # App entry point and middleware configuration
Pages/                  # Razor Pages
wwwroot/                # Static assets (CSS, JS, images)
appsettings.json        # App configuration
.github/workflows/      # GitHub Actions workflow
```
