---
title: "Free Setup Requirements & Checklist"
summary: "The structure is a generic Eleventy theme with the standard folder and file names."
eleventyNavigation:
  key: Free Setup Requirements & Checklist
  parent: 01-cloud-deploy-core
  order: 18
---
When you purchase a DevelopVIDeploy bundle or DevelopVIDeploy Core we can setup the Core plugin for you at your designated server provider. This service is free.

To get this done we’ll need some information from you. In some cases we’ll need user ids, passwords and, sometimes, your private SSH keys.

We’ll open up an installation ticket on our support system where you can safely submit this type of sensitive information – when the ticket is closed, the data is automatically deleted.

## Free Setup: What We’ll Need From You

*   Access to your cloud server provider account. If you’re using DigitalOcean you can invite [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) to your account. Otherwise, you can invite [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) to your account. (We will setup an email address for [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection)). Alternatively you can provide your login credentials to your cloud server provider account as long as it does not have 2FA enabled on it – you can enter those in the PRIVATE CREDENTIALS area of this ticket.
*   Access to your registrar or services where your DNS name servers are located. If you haven’t done so yet, we recommend that you use CloudFlare for your authoritative name servers. If you do use CloudFlare, please invite [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) to your account and ensure that you have provided full access. Full access is not the default so you’ll need to edit the permissions for [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection).
*   If you are not using CloudFlare for your DNS services, please invite [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) to your account. If your registrar does not support invitations you should add your login credentials to the private credentials area on the installation ticket.
*   Please let us know which domain or subdomain should be used to access the DevelopVIDeploy site.
*   Please let us know if you would like us to create new SSH key-pairs for you. If you prefer to use your existing key pairs you should add those to the private credentials area of the installation ticket. Otherwise we’ll create new key-pairs for you and provide them to you when setup is complete.
*   Please let us know which region we should use for your servers.
*   We’ll provision a 2-Core / 2 GB server. If you prefer a larger one let us know.

Note: The PRIVATE CREDENTIALS button is located in the button bar at the top of the installation ticket (next to the OPEN A TICKET button).

## Scope Of Work

Only the Core Plugin is setup for free (as long as the request comes in within the first 30 days of your initial license purchase). SaaS services such as setting up template sites, WooCommerce store, products, integration with Stripe and other payment providers etc. are not included in the free service.

- - -

## Paid SaaS Setup: What We’ll Need From You

If you have paid for one of our SaaS setup services we’ll need additional information from you (in addition to the items listed in the free section above)

*   Access to your transactional email provider (eg: mailgun). You can invite [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) to your account. Or, if that’s not supported, you can provide either the API keys and other credentials or your SMTP credentials – please add these to the Private Credentials area of the installation ticket.
*   Access to your STRIPE account. Please invite either [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) or [\[email protected\]](/web/20240420010534/https://wpclouddeploy.com/cdn-cgi/l/email-protection) to your account. If you’re not comfortable with that please add the stripe test keys (publishable and secret keys) to this ticket. We’ll then get back to you with the webhook that needs to be added to the test and live areas on stripe.
*   Access to your WooCommerce account where your WooCommerce Subscriptions plugin was purchased – please add these to the Private Credentials area of the installation ticket. If your account has 2FA enabled on it then you should download the WooCommerce Subscriptions plugin and add it to the installation ticket. Once we’ve completed the setup you can connect your account so that you’ll get update notifications from WooCommerce.

- - -

## Momentum Setup: What We’ll Need From You

If you have purchased a DevelopVIDeploy Momentum service package we’ll need additional information from you (in addition to the items listed in the two sections above).

*   Credentials for your OPENAI account. Please add these to the Private Credentials area of the installation ticket. Note: You must have funded your account with at least $50.00 and generated at least one API key (when you generate an API key they will likely ask you to verify a phone number which is why we cannot do this for you). These two actions will allow OpenAI to validate your account and eventually increase the rate limits on the API for you.
*   Your Gavity Forms license key (you’ll need a Gravity Forms ELITE license)
*   Your Gravity Perks **PRO** license key (gravitywiz.com)
*   Your Admin Menu Editor PRO license key

You can add the license keys to the Private Credentials area of the installation ticket.

If you have asked us to replicate the Momentum Marketing Demo site for you, we’ll need the following licenses as well:

*   Beaver Builder (PRO)
*   Beaver Themer
*   Powerpack for BuilderBuilder ([wpbeaveraddons.com](https://web.archive.org/web/20240420010534/https://wpbeaveraddons.com/))

- - -

### More Topics In Admin

*   [Restoring From AWS S3 Into A New Site or Server](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/tips-techniques-education/restoring-from-s3-into-a-new-site-or-server/)
*   [Backups With AWS S3](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/backups-with-aws-s3/)
*   [Restoring From Backup](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/restoring-from-backup/)
*   [6G Firewall (Deprecated)](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/6g-firewall/)
*   [7G Firewall](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/7g-firewall/)
*   [Native Linux Cron](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/native-linux-cron/)
*   [Disabling Sites](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disabling-sites/)
*   [Password Protect A Site (HTTP Authentication)](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-basic-password-protection-to-a-site-http-authentication/)
*   [One-click Login (AKA Passwordless Logins)](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/one-click-login-aka-passwordless-logins/)
*   [Remove/Delete Site](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/remove-delete-site/)
*   [Manage PHP Options](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/manage-php-options/)
*   [Add A WordPress Administrator](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/add-a-wordpress-administrator/)
*   [Notifications and Alerts](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/notifications/)
*   [Managing WordPress DEBUG Flags](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/managing-wordpress-debug-flags/)
*   [Object Cache: MemCached](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-memcached/)
*   [Object Cache: Redis](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/object-cache-redis/)
*   [Monit / Healing](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monit-healing/)
*   [DNS Integration: CloudFlare](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/dns-integration-cloudflare/)
*   [Site Packages](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-packages/)
*   [Site Update Plans](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-update-plans/)
*   [Site Expiration](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/site-expiration/)
*   [White Label Colors](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/white-label-colors/)
*   [Adding Custom NGINX Configs](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/adding-custom-nginx-configs/)
*   [Custom Servers (Bring Your Own Server)](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-servers-bring-your-own-server/)
*   [How To Change The IP Address For Your Server](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/how-to-change-the-ip-address-for-your-server/)
*   [Virtual Cloud Providers](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/virtual-cloud-providers/)
*   [Monitorix](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/monitorix/)
*   [File Manager](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/file-manager/)
*   [PHPMyAdmin - Database Operations](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/phpmyadmin-database-operations/)
*   [Using Remote Databases](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-remote-databases/)
*   [SMTP Gateway](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/smtp-gateway/)
*   [Server Updates](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/server-updates/)
*   [Theme & Plugin Updates](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/theme-plugin-updates/)
*   [Bulk Actions on Servers](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-servers/)
*   [Bulk Actions on Sites](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-actions-on-sites/)
*   [SSH Key Overrides](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/ssh-key-overrides/)
*   [Webserver Types](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/webserver-types/)
*   [DVI Cron Jobs](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/wpcd-cron-jobs/)
*   [Disk Quotas](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/disk-quotas/)
*   [Custom Post Type Quotas](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/custom-post-type-quotas/)
*   [Using Post-Processing Custom Bash Scripts](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/using-post-processing-custom-bash-scripts/)
*   [Bulk Copy To Server](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bulk-copy-to-server/)
*   [Copy To Server (Automated Daily Process)](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/copy-to-server-automated-daily-process/)
*   [Shortcodes](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/shortcodes/)
*   [Bootstrapping A WordPress Server With Our Scripts](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts/)
*   [Bootstrapping A WordPress Server With Our Scripts - Archive Version 4.x](https://web.archive.org/web/20240420010534/https://wpclouddeploy.com/documentation/wpcloud-deploy-admin/bootstrapping-a-wordpress-server-with-our-scripts-version-4-x/)
