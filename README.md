# Static blog using Github.io pages using ghost, cloudflare and github page

## Base routine
- Install NodeJS (including chocolatey): last supported version by Ghost is 18.12.1. 
- Install ghost-cli@latest (might have trouble with [powershell](https://www.c-sharpcorner.com/article/how-to-fix-ps1-can-not-be-loaded-because-running-scripts-is-disabled-on-this-sys/))
- Locate website Ghost folder and run "Ghost start" in it. If index.js is missing, create an empty folder, use "ghost install local" in it and copy the missing folder into your production folder. 
- Install wget using chocolatey "choco install wget"
- git clone https://github.com/itsignacioportal/ghost-static-site-generator/
- cd ghost-static-site-generator
- node src\index.js --url https://www.fabykun.st
- website content will be at /static/ folder, copy it and upload it in the github.io page

## Edit Ghost page
- Run "Ghost start"
- Connect using "http://localhost:2368/ghost/" url

### Changing CSS
Modifying css cannot be made by changing .css files, it needs to run through "Zip" to be compiled into the theme.
- Locate theme folder in VS Code (in my case it's "london")
- Run "npm install" at this location (in vsCode's terminal for example)
- Make changes to the css
- Run "npm run zip"

## Use Ghost CLI to edit
Locate your local website

## Enforce HTTPS on GitHub Pages with a Gandi domain name
Based on [Armand Grillet article](https://armand.gr/blog/posts/ghpages-gandi-cloudflare/):

Log in Cloudflare and then go to the “DNS” tab and copy the provided Cloudflare nameservers (add a site if needed).

Paste them in Gandi: <yourdomain.com>/nameservers/External domain names.

Follow [github guide to configure a subdomain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain) 

Create the CNAME record in Cloudflare (still in the DNS management section of your site).

Go to the “Page Rules” tab, create a rule on <yourdomain.com>/* where the settings are “Always use HTTPS”.

This should be enough to make your website accessible via HTTPS and even redirect users visiting http://<yourdomain.com> to the HTTPS equivalent.

You can change your SSL/TLS encryption mode on Cloudflare in the “SSL/TLS” tab. 
