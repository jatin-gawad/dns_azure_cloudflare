Sure, I can help you create a Markdown file with the content you provided. Here is the step-by-step guide formatted in Markdown:

```markdown
# Adding a Custom Domain and Updating Cloudflare for Production Environment

## Step 1: Understanding the Current Setup

### What is currently in place:
- The development environment has a custom domain (dev.lifeandeo.ca).
- In Cloudflare, a CNAME record with:
  - **Name:** dev
  - **Content:** Points to wig-lifeeando-dev-01.azurewebsites.net (Azure App Service default domain).
  - **Proxy:** Enabled (Orange Cloud), which routes traffic securely through Cloudflare.

This setup allows users to access the development environment via the custom domain while taking advantage of Cloudflare's features like caching, SSL/TLS, and security.

## Step 2: What Needs to Be Done for Production

To replicate this functionality for the production environment, we need to:
1. Add the custom domain (www.lifeandeo.ca or prod.lifeandeo.ca) to the production App Service in Azure.
2. Update the DNS settings in Cloudflare to direct traffic for the production domain to Azure App Service.

## Step 3: Steps to Add a Custom Domain to the Production App Service

### Access the Production App Service in Azure:
- Navigate to the Azure portal and select the production App Service (e.g., wig-lifeeando-prd-01).

### Add a Custom Domain:
- Go to the Custom domains blade in the App Service.
- Click on **Add Custom Domain** and enter the domain you want to use (e.g., www.lifeandeo.ca).

### Verify Domain Ownership:
- Azure will provide a TXT or CNAME record to verify ownership.
- In Cloudflare, add this record to your DNS settings:
  - **Type:** TXT or CNAME
  - **Name:** As specified by Azure (e.g., _acme-challenge.www.lifeandeo.ca).
  - **Content:** Value provided by Azure.
- Wait for Azure to verify the domain. This may take a few minutes.

### Bind the Custom Domain:
- Once verified, Azure will bind the domain to the production App Service.

## Step 4: Update Cloudflare DNS Settings

### Add CNAME Record for Production:
- In Cloudflare, navigate to the DNS settings for the domain.
- Add a new record:
  - **Type:** CNAME
  - **Name:** www (or prod, depending on your naming convention).
  - **Content:** Azure's App Service default domain for production (e.g., wig-lifeeando-prd-01.azurewebsites.net).
  - **Proxy Status:** Proxied (Orange Cloud).

### Ensure SSL/TLS is Configured:
- In Cloudflare, set SSL/TLS mode to Full or Full (Strict).
- This ensures end-to-end encryption between Cloudflare and Azure.

## Step 5: Testing the Setup

### Verify DNS Resolution:
- Use tools like nslookup or online DNS checkers to ensure the CNAME record resolves to Azure's default domain.

### Test in Browser:
- Access the custom domain (e.g., www.lifeandeo.ca) and ensure it redirects correctly to the production App Service.

### Check HTTPS:
- Confirm the domain is accessible over HTTPS with a valid certificate.
```

You can copy and paste this content into a `.md` file. Let me know if you need any further assistance!