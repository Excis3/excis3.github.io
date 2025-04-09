---
title: "AZURE Subdomain takeover on azurewebsites.net"
date: 2025-04-09 01:00:00 +0200
categories:
  Vulnerabilities
  Subdomain-Takeover
tags:
  azure
  azurewebsites
pin: true
mermaid: true
image:
  path: /Excis3/excis3.github.io/main/media/azure-sdto-appservice.webp
---

In this post, I’ll walk you through how to perform a **subdomain takeover** on an unclaimed `azurewebsites.net` app. This guide includes screenshots, command-line examples, and a Python-based approach for automation.

First, I’ll show you how to manually claim the subdomain via the Azure portal. Then, we’ll move to a Python-based method to automate the process. My motivation for this research was to integrate the process into my automation workflow. Since there wasn’t a clear, consolidated resource, I ended up reading dozens of blog posts and technical documents before piecing it all together.

> **Recap:**  Many companies point (sub)domains to cloud services via DNS records. When those cloud resources are deleted, the DNS records often remain. This opens the door for attackers to re-create the missing cloud resource and take control over the subdomain. Since the DNS record still points to the service, the domain traffic is now routed to the attacker’s asset.
{: .prompt-info }

---

## Taking Over an `azurewebsites.net` Application

Let’s say you’ve identified a CNAME DNS record pointing to an unclaimed Azure Web App. In this case, we’ll use:

- **Domain:** `subdomain.excis3.be`
- **Azure App:** `sdto-poc-excise.azurewebsites.net`

This Azure resource has been deleted, but the DNS CNAME is still active, making it ripe for takeover.

Running the following command confirms the DNS is pointing to Azure:

```bash
dig -t cname +short subdomain.excis3.be
```
However, opening the domain in a browser returns an error, proof the resource doesn’t exist.

![3_Digcommand.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/3_Digcommand.png)
![4_Unresolved-host.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/4_Unresolved-host.png)

### Using the Azure Portal (GUI)

To begin, log in to the Azure Portal at [https://portal.azure.com](https://portal.azure.com). In the search bar at the top, type **App Services** and select it from the results.

![1_App-Services.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/1_App-Services.png)

Once in the App Services section, click on **Create → Web App** in the top left corner. This is where we'll attempt to re-register the unclaimed resource and deploy our PoC (Proof of Concept) application.

![2_Create_menu.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/2_Create_menu.png)

You’re now in the **Create Web App** form. The most important field here is the **App name** under **Instance Details**. Enter the subdomain prefix (the part before `.azurewebsites.net`) to check if the name is still available. Be sure to **uncheck** the option **Try a secure unique default hostname**, as this feature is designed to prevent subdomain takeovers (SDTOs).

![5_registername.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/5_registername.png)

Once the name is verified as available, proceed to configure the application for your PoC.

- Select **Python 3.13** as the runtime stack.
- Leave the OS as **Linux** (a cost-effective choice).
- Choose your preferred **region**.
- For pricing, select **Basic B1**. Avoid the Free plan—it doesn’t allow custom domains.

> 💡 Ignore the screenshot below showing the Free plan. Use Basic B1 for full functionality.

![6_Pricingplan.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/6_Pricingplan.png)

With everything set up, click **Review + Create**, then **Create**. Azure will begin deploying your application. After deployment, you’ll see a success screen with a green checkmark. Click **Go to resource** to continue configuration.

![7_createapp.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/7_createapp.png)

At this point, visiting the app URL will display a 404 error. That’s expected—no content has been deployed yet.

![8_404page.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/8_404page.png)

---

### Linking Your Custom Domain

In the **Overview** tab of your Web App, look for the **Add custom domain** option in the middle of the page. Click it to add your domain (e.g., `subdomain.excis3.be`).

On the domain setup page:

- Click **Add custom domain**.
- Choose **All other domain services** as the provider.
- Enter your domain and click **Validate**.

![9_customdomain.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/9_customdomain.png)

You may be prompted to add a TXT record for domain verification. This is a protective feature, but often neglected—making SDTOs possible. Once the domain is validated, it will appear with a green status.

![10_validation.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/10_validation.png)

---

### Hosting the PoC via GitHub

To deploy a basic Python app:

1. Fork this repository: [https://github.com/Azure-Samples/python-docs-hello-world](https://github.com/Azure-Samples/python-docs-hello-world).
2. Customize the content to reflect your PoC message.

Here’s a simple version of what I used:

![11_poccode.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/11_poccode.png)

Now, return to your Azure Web App and go to **Deployment Center** in the left-hand menu. Choose **GitHub** as your deployment source and authorize your GitHub account.

![12_deployment.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/12_deployment.png)

- Select your GitHub **username** (as organization).
- Choose the **repository** you forked.
- Pick the **branch** (usually `main`).
- Click **Save** to begin deployment.

Once you see a **Success** status, your app is live.

![13_config.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/13_config.png)

Visit `subdomain.excis3.be` to confirm your PoC is now hosted on the targeted subdomain.

![14_takeover.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/14_takeover.png)

---

### Cleaning Up

Once you’ve validated the PoC and documented the takeover, don’t forget to clean up the resources to avoid unnecessary charges.

1. Navigate to your **Dashboard**.
2. Search for **All Resources**.
3. Select all associated resources.
4. Click **Delete**, then confirm in the sidebar.

![15_allservices.png](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/15_allservices.png)

---  

## Takeovers with Python

Code snipits to take over with python

## Report template for bugbounty hunters

Template

## Conclusion

Conclusion
