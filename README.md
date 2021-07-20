# Turn-it-Around
Migration of turnitaround.org to WordPress from Drupal. Project goals - provide the partner with increased control over the day to day running of the site, provide a refreshed design utilising their revised brand guidelines, ultimately provide the partner with a platform to become a national resource. Project deployment deadline is October 19th. 

## Development

### Getting Started 

### Local Development

### Testing

### Contributing

## Deployment
#### Add Theme Footer Credits
- [ ] "Proudly powered by WordPress" link to WordPress.com (no credit on memorial-type sites)
- [ ] If hosted on Pressable, add "Hosted by Pressable" link to: https://pressable.com/?utm_source=Automattic&utm_medium=rpc&utm_campaign=Concierge%20Referral&utm_term=concierge 

#### Development QA
- [ ] Run the site through WebPageTest.org and address any front-end performance issues that get a grade lower than B.  
- [ ] Check that the site works as expected on mobile and all supported modern browsers. 
- [ ] Confirm core and all plugins up to date. 
- [ ] Confirm SSL in place and any mixed content warnings have been addressed or confirm how and when the SSL certificate will be generated during the final cutover. 
- [ ] Confirm 404s handled properly (are custom 404 pages in place?). 
- [ ] Configure any additional analytics services (Google, etc). 
- [ ] If site is coming from another WordPress environment, ensure all key options/settings have been migrated to the new site (e.g. Discussion settings, time/date format, timezone, custom user roles, etc...) 
- [ ] Check that contact forms, WooCommerce, and other user-initiated notifications go to the client instead of concierge@wordpress.com. 
- [ ] Has the partner been informed about Jetpack Enhanced Distribution

#### Final Testing and Environment Setup
- [ ] If on Pressable, confirm that the site being launched uses the proper naming convention: [REPOSLUG]-production.mystagingwebsite.com. If not, set up a new site with the proper naming convention, clone the site you've been working on into it, and plan on launching the new site. Make sure it is connected to the correct branch in GitHub and connected to DeployHQ. Ping the Cascade team with questions.
- [ ] Check that Jetpack installed and connected (use https://jetpack.com/support/debug/ or confirm manually).
- [ ] Check Jetpack settings line up with expected behavior, e.g. turn off "Users must be registered and logged in to comment" setting if comments will be open to public (reference).
- [ ] Be sure that the Team 51 Plugin Autoupdate Filter plugin is installed and activated.
- [ ] Confirm VaultPress or Jetpack Backup are in place (use https://jetpack.com/support/debug/ or confirm manually).  
- [ ] Review the blog RC and confirm the site flagged as a Team 51 site. 
- [ ] Flag the site as Team 51 using our internal tool: https://mc.a8c.com/tdiv/team-51/ 
- [ ] Confirm our team's user (or the client, in some cases) own the site in Network Admin. 
- [ ] Reduce TTLs for A records in advance.  
- [ ] Confirm users practicing good security hygiene: only necessary users are Administrators, Two Factor Authentication is enabled (require Two-Step Authentication via WP.com SSO. Template for user guide here: https://docs.google.com/document/d/1FIdLVj0h13_R7A1x2oJPFDguGXXkfRWG6vi2TnJYRZU/edit?usp=sharing).  
- [ ] Check for any secondary mapped domains, and, if there are, plan for mapping them to the new site. 
- [ ] Migrate any relevant redirects from the previous site. 
- [ ] Check mail records and plan for moving any email suites associated with the domain if needed.  
- [ ] Delete any non-production-ready pages and posts (or set to private). 

If using WooCommerce, include the following: 

- [ ] Shipping: Add shipping extension 
- [ ] Shipping: Set origin postal code 
- [ ] Shipping: Add product dimensions (including weight) where necessary to products 
- [ ] Shipping: Confirm shipping zones 
- [ ] Shipping: Set up any necessary APIs (like FedEx, etc.) 
- [ ] Confirm tax settings 
- [ ] If using PayPal Standard, be sure that both "PayPal email" and the "Receiver email" fields have a valid and activate PayPal account associated with them.
- [ ] If using subscriptions, confirm settings 
- [ ] Configure any coupons needed at launch 
- [ ] Confirm inventory settings 
- [ ] Confirm product settings 
- [ ] Confirm review settings 
- [ ] Confirm cart behavior 
- [ ] Confirm Email content (for various contexts) 
- [ ] Confirm recipients (for various contexts) 
- [ ] Establish migration plan for legacy data (if needed)

#### Confirm Launch Schedule/Launch Planning
- [ ] Confirm launch date and time with partner. 
- [ ] Confirm dates of any content freeze and/or delta migration. 
- [ ] Confirm access to key login credentials: DNS, wp-admin, CDNs like Cloudfront, hosting control panels, etc. 
- [ ] Confirm DNS config for the primary domain, noting any additional DNS records that need to be preserved (ex: MX records, subdomains) 
- [ ] (Internal) Put date an time of launch on team calendar 
- [ ] Start a list of critical things that need to be tested immediately after the launch; key functionality, search, 404s, sitemaps, social sharing, search engine crawlability, analytics tools are recording traffic, etc. 
- [ ] Make a list of any non-Pressable staging URLs or file URLs which may need to be search/replaced at launch, such as contractor agency dev sites or  wordpress.com files urls
- [ ] Test site in Facebook Open Graph Debugger and Sharing Debugger, address any issues. 
- [ ] Test site in Twitter Card Validator, address any issues. 
- [ ] Confirm ownership and availability for any post-launch fixers, search-and-replace, or other launch day tasks. 

If using WooCommerce, include the following: 

- [ ] Create/Deliver documentation for how to cancel/edit/manually add orders 
- [ ] Create/Deliver documentation for shipment tracking 
- [ ] Ask Partner to verify inventory is correct for launch 
- [ ] Perform final tests and verify functionality 
- [ ] Turn off test mode in all payment service extensions 
- [ ] If site is using Stripe, verify `production url +  /?wc-api=wc_stripe` is set at https://dashboard.stripe.com/account/webhooks  

#### Launch the site
- [ ] Take a screenshot of the old site. 
- [ ] Set search indexing to on (remove robots txt) and/or remove private site settings (if applicable. 
- [ ] Map domain or add domain as primary via Pressable settings. 
- [ ] For Pressable sites using domain-only WordPress.com accounts, add the primary (non-www) TXT record generated by Pressable (the one prefixed with atomic-domain- to the DNS to tell WP.com to look at Pressable for the domain instead of WP.com. (Do not add the www TXT record to WP.com DNS because that will interfere with the *.domain.TLD CNAME record that handles www for WP.com sites). 
- [ ] Run any post-launch import fixing steps. 
- [ ] If site is using YOAST, regenerate index: https://developer.yoast.com/features/wp-cli/reindex-indexables/
- [ ] If site will be using VideoPress, turn on "Enable high-speed, ad-free video player" in Jetpack. 
- [ ] DNS changes. 
- [ ] Confirm SSL or force cert generation (Internal only: If on WordPress.com, force SSL cert generation from DARC). 
- [ ] Find/replace to reflect primary domain, confirm via source viewing, post content searching. Use https://wordpress.org/plugins/better-search-replace/ and do a dry run first. For Pressable sites,replace references to the “mystagingwebsite” or other development domains 
- [ ] (Pressable sites) Toggle CDN setting to ON ("site optimization for static resources like images, CSS, and JavaScript")
- [ ] Clear caches. 
- [ ] (Internal only) Sitemap regeneration (run `wp jetpack sitemap rebuild –purge` if sitemap doesn’t appear within a few minutes of launch) 
- [ ] Confirm analytics services (stats, Google, etc) are working as expected. 
- [ ] Go through list of critical things to test, cross them off as you do. 

If using WooCommerce, include the following: 

- [ ] Do final migration of customer/sales/product data from old site to new site 

#### Internal A8C: Post-launch / Communications
- [ ] Confirm site is loading (www and non-www) with proper SSL cert and there’s no mixed content warnings 
- [ ] Check both http and https protocols. As there should be a redirect in place for the http.
- [ ] Confirm launch and make sure site-owner or key admin is able to login to the site and has related documentation for managing their site, and that they know where to turn for support. 
- [ ] Set up a development environment with current data, theme, plugins, etc. so we can quickly test changes before making them live; connect Jetpack (plan should match prod site); set dev site to discourage search engines/crawlers (via Settings). If on Pressable, here is the CLI command (the Site ID is at the end of the Pressable URL in the control panel) : team51 create-development-site --site-id=NNNNNNNN 
- [ ] (A8C Only) In Zoho, set the Project entry Status to “Launched” and populate the “Completion Date.” 
- [ ] Take a screenshot of the new site. 
- [ ] (A8C Only) Post a #launched or #migrated note on our team p2 and include the old and new screenshots; cross post to specialprojectslaunched; cross post to woomarketingp2 if the launch includes a major WooCommerce integration and/or other specific product p2s if a product was used prominently on the site; cross post to customerstoriesp2 if the site owner is a good fit to be featured there
- [ ] (A8C Only) Update relevant P2 posts to note that the site has launched (including updating dev/prod site URLs on project P2). 
- [ ] Raise the DNS TTL where applicable. 
- [ ] Remove any un-needed plugins used for migration, import,  find/replace work, or that a developer may have installed during development that is no longer needed. 
- [ ] In Jetpack, set all possible plugins to autoupdate in Calypso using a a8cteam51 user support session. 
- [ ] Remove any individual contractor accounts from Pressable, GitHub, /wp-admin, or any other tools shared with them throughout the build process. Rotate passwords on any team accounts where access was shared. 

#### Additional steps for WordPress.com (simple or VIP) to-Pressable Migrations:
- [ ] Ensure stats and followers are migrated from the WordPress.com site to the Jetpack site. https://jetpack.com/support/subscription-migration-tool/ 
- [ ] Add the primary (non-www) TXT record generated by Pressable (the one prefixed with atomic-domain- to the DNS to tell WP.com to look at Pressable for the domain instead of WP.com. (Do not add the www TXT record to WP.com DNS because that will interfere with the *.domain.TLD CNAME record that handles www for WP.com sites). 
- [ ] Is there an existing Akismet key for the site and should it be transferred over to maintain site-specific learning?

### Env Vars / Config

## Help

## License
