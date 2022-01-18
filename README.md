# Google Personal/Shared Drive Index

[![Year](https://data.jsdelivr.com/v1/package/npm/@googledrive/index/badge/rank)](https://www.jsdelivr.com/package/npm/@googledrive/index)
[![Year](https://data.jsdelivr.com/v1/package/npm/@googledrive/index/badge/year)](https://www.jsdelivr.com/package/npm/@googledrive/index)
[![Month](https://data.jsdelivr.com/v1/package/npm/@googledrive/index/badge/month)](https://www.jsdelivr.com/package/npm/@googledrive/index)
[![Week](https://data.jsdelivr.com/v1/package/npm/@googledrive/index/badge/week)](https://www.jsdelivr.com/package/npm/@googledrive/index)
[![Day](https://data.jsdelivr.com/v1/package/npm/@googledrive/index/badge/day)](https://www.jsdelivr.com/package/npm/@googledrive/index)
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://www.npmjs.com/package/@googledrive/index)

## Full White label and Customizable Index | One of a kind

* Supports Both My and Team/Shared Drives with Dark Mode.
* Click https://bdi-generator.hashhackers.com to make yours or watch https://youtu.be/Ihk4Gm3DPvg.

## Read Wiki of Index before asking How to Do What...

* [Getting-Started-with-Google-Drive-Index](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/wikis/Getting-Started-with-Google-Drive-Index)

[![Screenshot](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/raw/master/images/themes/vapor.png)](https://youtu.be/Ihk4Gm3DPvg)

[![Screenshot](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/raw/master/images/themes/darkly.png)](https://youtu.be/Ihk4Gm3DPvg)

`Note: The Changes in your worker's config can affect late due to cache. Use incognito mode every time to open the worker URL to overcome that issue.`

## How to

* Stable Release `2.1.3`
* Latest Index is faster than before, but backup before making new, and report if I missed something in issues. :)
* Beta Version (Latest) - [bdi-generator](https://bdi-generator.hashhackers.com) (For Dark Theme use darkly)
* If you want to deploy main drive leave the option ROOT as it is.
* If you want to deploy your Team Drive/Shared Drive/Folder then copy the ID and replace it with ROOT.
* Eg. if you open this shared drive `https://drive.google.com/drive/u/0/folders/0AOM2i7Mi3uWIUk9PVA` - `0AOM2i7Mi3uWIUk9PVA` is its ID.
* Authenticate and copy the code from Google and paste it into Authorization Code Box.
* Click on Get Code to Generate Code and Copy it for later use.
* Now Create Cloud flare account and verify email or login with existing account.
* Find Workers and Open it.
* Create your sub-domain or continue if already done.
* Select the Free Plan.
* Click on Create a Worker.
* You can rename the workers at top of the page.
* Now paste the code you copied before.
* Click on Save and Deploy.
* Done. (May take time for some users due to new account or cache issues)
* [Watch Video](https://youtu.be/Ihk4Gm3DPvg)

## Use Case and Workers needs to be used

* If you're new and noob, just use [this](https://bdi-generator.hashhackers.com). Doesn't support FOLDER Id anymore.
* Simple Index with Normal or Service Account, use [this](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/blob/master/worker/worker-super.js). (Can search all drives and display drive only links if enabled) Doesn't support FOLDER Id anymore.
* If you enable Second Domain option, you need to make additional Cloudflare workers and account using [this](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/blob/master/worker/worker-second-domain.js). Doesn't support FOLDER Id anymore.
* Advanced Index to Search All Drives and Handle Search and Display Index Links, use [this](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/blob/master/worker/worker-multiple-drives.js). (make sure you add Service Account to those drives, which you're adding inside Index Code)
* [This](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/blob/master/worker/worker-legacy.js) is old code, slower and with errors. Use this only if you want to use FOLDER Id.

## Drive ID Types

* My Drive is `root`, eg. Drive of Simple Gmail Account.
* Shared Drive ID is Team/Shared Drive IDs Root.
* Folder ID is those which are not root and you create a folder and use it's ID. If you use this, this will work good in legacy as it'll not display search because Google Drive doesn't support Folder Only search. AVOID USING FOLDER IDs.

## Steps for Making Search All Drives Index

1. Copy Code from [here](https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index/-/raw/master/worker/worker-multiple-drives.js).
2. Make a Single Service Account (Fresh and New)
3. Add that SA Email to drives, only to those, which you want to Index. and change "service_account": false, to "service_account": true,
4. Add that Service Account to Index
5. In domains_for_dl = ['']; enter your Index URL, that you're making now. eg. `https://example.com`
6. Add your Drive IDs in Index Code
7. Change `"second_domain_for_dl": false`, to `"second_domain_for_dl": true`, (don't forget to deploy second domains worker.)

## authConfig

````
"siteName": "Bhadoo Drive Index", // Website name
"client_id": "746239575955-oao9hkv614p8glrqpvuh5i8mqfoq145b.apps.googleusercontent.com", // Client id from Google Cloud Console
"client_secret": "u5a1CSY5pNjdD2tGTU93TTnI", // Client Secret from Google Cloud Console
"refresh_token": "", // Authorize token
"service_account": false, // true if you're using Service Account instead of user account
"service_account_json": randomserviceaccount, // don't touch this one
"files_list_page_size": 50,
"search_result_list_page_size": 50,
"enable_cors_file_down": false,
"enable_password_file_verify": true, // support for .password file
"enable_virus_infected_file_down": true, // support for downloading virus infected files
"direct_link_protection": false, // protects direct links with Display UI
````

## Basic Config

````
    "roots":[
      {
          "id": "root",
          "name": "Drive One",
          "protect_file_link": false,
         // "auth": {"username":"password"} /* Remove double slash before "auth" to activate id password protection */
      },
    ]};
````

## Multiple ID Config

* Add this code for each drive. see cloud flare workers code for more info. (requires common sense)

````
    "roots":[
      {
          "id": "root",
          "name": "Drive One",
          "protect_file_link": false,
         // "auth": {"username":"password"} /* Remove double slash before "auth" to activate id password protection */
      },
      {
          "id": "root",
          "name": "Drive Two",
          "protect_file_link": false,
         // "auth": {"username":"password", "username1":"password1"} /* Remove double slash before "auth" to activate id password protection */
      },
    ]};
````

## Service Account

* Multiple Service Accounts are supported.
* set `"service_account": false` to `"service_account": true`
* Replace {} with data from service account `file.json`

## Multiple Users Password

* For single user

````
            // "auth": {"username":"password"} /** remove double slash at starting of this line to use password. */
````

* For multiple users (unlimited users)

````
      {
          "id": "",
          "name": "Drive Two",
          "protect_file_link": false,
          // "auth": { "user1":"pass1", "user2":"pass2", }  /** remove double slash at starting of this line to use password. */
      },
````

* where `"user1":"pass1"` and `"user2":"pass2"` are combinations.
* if users adds `"auth":{"":""}` empty values then the site will ask for authentication but user can enter without entering any data by clicking submit.

## Use of .password File

* This is directory encryption added by the original author.
* Add a .password file your required password in your folder which you want to protect, each folder should have its own .password file.
* The password is stored inside the Google Drive Folder, not the index and the .password file is hidden an cannot be accessed using Index.
* Example use https://bit.ly/3tBxXJN and password is `thispassword`

## Brand Customization

* In Latest Release, you can rebrand the Index as per your needs.
* Each line has its own custom feature. Edit as per your needs.
* You can remove credit option but we request you not to.
* See Below code to understand Customization.

````
const uiConfig = {
    "theme": "slate", // switch between themes, default set to slate, select from https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index
    "version": "2.1.3", // don't touch this one. get latest code using generator at https://bdi-generator.hashhackers.com
    // If you're using Image then set to true, If you want text then set it to false
    "logo_image": true, // true if you're using image link in next option.
    "logo_height": "", // only if logo_image is true
    "logo_width": "100px", // only if logo_image is true
    "favicon": "https://cdn.jsdelivr.net/npm/@googledrive/index@2.1.3/images/favicon.ico",
    // if logo is true then link otherwise just text for name
    "logo_link_name": "https://cdn.jsdelivr.net/npm/@googledrive/index@2.1.3/images/bhadoo-cloud-logo-white.svg",
    "fixed_header": true, // If you want the footer to be flexible or fixed.
    "header_padding": "60", // Value 60 for fixed header, Value 20 for flexible header. Required to be changed accordingly in some themes.
    "nav_link_1": "Home", // change navigation link name
    "nav_link_3": "Current Path", // change navigation link name
    "nav_link_4": "Contact", // change navigation link name
    "show_logout_button": false, // shows logout button if auth0.com is active
    "fixed_footer": false, // If you want the footer to be flexible or fixed.
    "hide_footer": true, // hides the footer from site entirely.
    "header_style_class": "navbar-dark bg-primary", // navbar-dark bg-primary || navbar-dark bg-dark || navbar-light bg-light
    "footer_style_class": "bg-primary", // bg-primary || bg-dark || bg-light
    "css_a_tag_color": "white", // Color Name or Hex Code eg. #ffffff
    "css_p_tag_color": "white", // Color Name or Hex Code eg. #ffffff
    "folder_text_color": "white", // Color Name or Hex Code eg. #ffffff
    "loading_spinner_class": "text-light", // https://getbootstrap.com/docs/5.0/components/spinners/#colors
    "search_button_class": "btn btn-danger", // https://getbootstrap.com/docs/5.0/components/buttons/#examples
    "path_nav_alert_class": "alert alert-primary", // https://getbootstrap.com/docs/4.0/components/alerts/#examples
    "file_view_alert_class": "alert alert-danger", // https://getbootstrap.com/docs/4.0/components/alerts/#examples
    "file_count_alert_class": "alert alert-secondary", // https://getbootstrap.com/docs/4.0/components/alerts/#examples
    "contact_link": "https://telegram.dog/Telegram", // Link to Contact Button on Menu
    "copyright_year": "2050", // year of copyright, can be anything like 2015 - 2020 or just 2020
    "company_name": "Bhadoo Cloud", // Name next to copyright
    "company_link": "https://telegram.dog/Telegram", // link of copyright name
    "credit": true, // Set this to true to give us credit
    "display_size": true, // Set this to false to hide display file size
    "display_time": false, // Set this to false to hide display modified time for folder and files
    "display_download": true, // Set this to false to hide download icon for folder and files on main index
    "disable_player": false, // Set this to true to hide audio and video players
    "custom_srt_lang": "", // Subtitle Language Code for Custom .vtt language.
    "disable_video_download": false, // Remove Download, Copy Button on Videos
    "second_domain_for_dl": false, // If you want to display other URL for Downloading to protect your main domain.
    "downloaddomain": domain_for_dl, // Ignore this and set domains at top of this page after service accounts.
    "poster": "https://cdn.jsdelivr.net/npm/@googledrive/index@2.1.3/images/poster.jpg", // Video poster URL or see Readme to how to load from Drive
    "audioposter": "https://cdn.jsdelivr.net/npm/@googledrive/index@2.1.3/images/music.jpg", // Video poster URL or see Readme to how to load from Drive
    "jsdelivr_cdn_src": "https://cdn.jsdelivr.net/npm/@googledrive/index", // If Project is Forked, then enter your GitHub repo
    "render_head_md": true, // Render Head.md
    "render_readme_md": true, // Render Readme.md
    "display_drive_link": false, // This will add a Link Button to Google Drive of that particular file.
    "plyr_io_version": "3.6.4", // Change plyr.io version in future when needed.
    "plyr_io_video_resolution": "16:9", // For reference, visit: https://github.com/sampotts/plyr#options
    "unauthorized_owner_link": "https://telegram.dog/Telegram", // Unauthorized Error Page Link to Owner
    "unauthorized_owner_email": "abuse@telegram.org", // Unauthorized Error Page Owner Email
    "arc_code": "jfoY2h19", // arc.io Integration Code, get yours from https://portal.arc.io
    "search_all_drives": false // gives gdrive links on search and searches all drives on that account, doesn't require adding
};
````

## Auth0 Integration  

* Please Note that auth0.com Free Plan allows 7000 active members per month only. Active members are those who have logged in once in that particular month.
* Cloudflare KV is used by this method, in Free Workers Plan, it's very limited and you cannot use it much, to avoid this ask your users to login and not clear the site cookies unless important. We suggest you upgrade to 5 USD plan of Workers if you face quota exceeded error on Cloudflare.
* Make a auth0.com account and while signup select advanced settings so you can edit the tenant name.
* Tenant Name looks like this hashhackers.auth0.com where you can have your own sub-domain on auth0.com, then verify your email.
* In Applications, Make New App, and select `Regular Web Applications`.
* In the app, go to settings and from there you can copy your client id and secret to be used on Cloudflare.
* Scroll down and see option `Allowed Callback URLs`, enter your website or workers URL that you will use for Index in following manner.
* `https://example.com/auth`, make sure you enter `https://` and `/auth`.
* Scroll down and see option `Allowed Logout URLs`, enter your website address where you would like to redirect when user logs out.
* Now In Authentication, Go to Database and open the Database that is shown there, You will see option `Disable Sign Ups` to stop username and password signup option when needed.
* In Authentication, you can go to `Social` and setup social login.
* To disable signup using Social Networks, if you wish to do that one day, go to `Auth Pipeline` and then `Rules`. Create New Rule, and find the Rule Template for `Disable social signups`. Add your App Client ID in the line number 2, then save it.
* Now come back to Cloudflare, and in Index code, enable auth0 with option true.
* Now enter Tenant Domain, make sure to use `https://` eg. https://example.auth0.com
* Enter your Client Id, Secret, Index Callback URL with `/auth` and Logout URL.
* Now in Cloudflare, there is a option for `Workers KV`, Create Namespace with any name, suggested is `AUTH_STORE_NS`.
* Now go to your worker for index, Click on Settings, then Click on Variables, at the end of the page you'll see `KV Namespace Bindings`, Enter variable name `AUTH_STORE` and then select the Name Space you created and Save it.
* It's done. If you face any problem, Go to [Index Discussion Group](https://t.me/+u-KpgiLT4r82Yzhh) and ask your question with full details, where you're stuck. Before that please try doing this yourself.

## Second Domain Systems

* set second_domain_for_dl to `true` first.
* set downloaddomain to your new index you're going to make below.
* then make separate index on different cloudflare account with worker-beta-second-domain.js code.
* change only refresh_token or SA and Drive IDs, don't touch anything else.
* It's done.

## arc.io Integration

* arc.io is embedded in code to support gdi.js.org
* if you have approved arc.io account, use your code.
* incase you don't have arc account and want to support us, please keep our arc.io code in your index.
* if anyone doesn't want to support us and want to remove arc, remove L140 line from the workers code.

## Themes

* There are 25 Themes from [bootswatch](https://github.com/thomaspark/bootswatch) official [Bootstrap](https://getbootstrap.com) Themes.
* You can check Theme from [bootswatch.com](https://bootswatch.com) before selecting.
* To Change theme, first generate the code, paste in Cloud flare Workers and then select one theme code from below and paste it in line 61 of worker script.

| Themes    |         |         |         |        |          |
|-----------|---------|---------|---------|--------|----------|
| cerulean  | cosmo   | cyborg  | darkly  | flatly | journal  |
| litera    | lumen   | lux     | materia | minty  | pulse    |
| sandstone | simplex | sketchy | slate   | solar  | spacelab |
| superhero | united  | yeti    | vapor   | morph  | quartz   |    
| zephyr    |

## Audio and Video

* Poster for Video is added as default.
* Fetch Video Poster from Google Drive, uses default if none available.

## Search Limitations

* Search only works if you use Shared Drive ID or root.
* Search won't work or the bar won't appear if you're using Folder ID inside from root or Shared Drive.

## Sorting by Name or Modified Time

* Find `params.orderBy` in workers code L623 and L710.
* use `params.orderBy = 'folder,name,modifiedTime desc';` to sort by File and Folder Name.
* use `params.orderBy = 'folder,modifiedTime desc,name';` to sort by Modified Time.
* A comma-separated list of sort keys. Valid keys are 'createdTime', 'folder', 'modifiedByMeTime', 'modifiedTime', 'name', 'name_natural', 'quotaBytesUsed', 'recency', 'sharedWithMeTime', 'starred', and 'viewedByMeTime'. Each key sorts ascending by default, but may be reversed with the 'desc' modifier. Example usage: ?orderBy=folder,modifiedTime desc,name. Please note that there is a current limitation for users with approximately one million files in which the requested sort order is ignored.

## Making your own repo, editing and making changes

* Fork this Repo or Import.
* Make your changes in `app.js` and `workers-beta.js` files.
* Make a new release in GitHub.
* Change jsDelivr CDN URL and version code in `workers-beta.js`.
* Deploy in Cloud flare Workers.

## Get Google_Client_ID and Secret and Generate Token

* Open [Google Dev Credentials Site](https://console.developers.google.com/apis/credentials).
* Create a Project, name as you like.
* Enable [Drive API](https://console.developers.google.com/apis/library/drive.googleapis.com)
* In [Credentials Page](https://console.developers.google.com/apis/credentials) Click `Create Credentials` and then Click `OAuth Client ID`.
* Click Configure Consent Screen.
* Select External.
* Fill your APP Details
* Select Scope as `https://www.googleapis.com/auth/drive` (wait few hours if Google Drive is not showing up if you've just enabled the scope) or
* You can also enter manual scope `https://www.googleapis.com/auth/drive` and click on add to table and then save or update.
* Proceed with Save and Continue.
* Add your email id you want to use as test user, up to 100 emails maximum. (Because you are not verified)
* In [Credentials Page](https://console.developers.google.com/apis/credentials) Click `Create Credentials` and then Click `OAuth Client ID`.
* Select Desktop App.
* Now you have your own CLIENT ID and CLIENT SECRET.
* Copy your details and save for future use.
* Copy worker-generator.js code.
* Replace Line 20 and 21 with your own CLIENT ID and CLIENT SECRET.
* Paste this code in Cloud flare Workers and follow the site.

## Upcoming Changes

* Adding More Features from other Indexes.

## Other Indexes

* List of Few [Indexes](https://github.com/alx-xlx/goindex)

## Credits

* Base Source: [maple3142](https://github.com/maple3142/GDIndex) and [yanzai](https://github.com/yanzai/goindex)
* CSS: [Bootstrap](https://getbootstrap.com) and [Bootswatch](https://bootswatch.com)
* API: [Google Drive API](https://developers.google.com/drive/api)
* [jQuery](https://jquery.com)
* PDF Viewer: [pdf.js](https://github.com/mozilla/pdf.js)
* Audio and Video Player: [plyr.io](https://github.com/sampotts/plyr)
* CDN: [jsDelivr](https://www.jsdelivr.com)
* Minified JS: [Toptal](https://www.toptal.com/developers/javascript-minifier)
* Obfuscator: [JavaScript Obfuscator Tool](https://obfuscator.io)
* Hosting: [Gitlab](https://gitlab.com) and [npm](https://www.npmjs.com)
* Website Hosting: [js.org](https://js.org) and [GitHub](https://github.com)
* Dev Editor Used: [ATOM](https://atom.io)
* Made for: [Cloudflare Workers](https://workers.cloudflare.com)
* Several Different Fixes by [SpEcHiDe](https://github.com/SpEcHiDe), [Adnan Ahmad](https://gitlab.com/viperadnan), [Prashanth C A](https://github.com/Achrou/goindex-theme-acrou/pull/176), [cheems](https://github.com/cheems/goindex-extended/blob/master/index.js#L553) and Unmentioned Forgotten Contributors.

## Disclaimer

* This project is not associated with Google, this project uses Google Drive API to Index Files and Folders.
* These Index's are written by someone else, possibly by donva and [maple3142](https://github.com/maple3142/GDIndex).
* Beta Version is redesigned using Bootstrap from Alpha Version by [Parveen Bhadoo](https://twitter.com/ParveenBhadoo).
* This Repo was imported from [yanzai](https://github.com/yanzai/goindex) and then modified for personal use.

## Support this Project

[![Support](https://cdn.buymeacoffee.com/buttons/v2/default-white.png)](https://www.buymeacoffee.com/bhadoo)

* Contribute to this project or improve this README.

### Donate by Crpto

* ETH `0xaf25cdc7967213172a745453a64e8a0b59686729`
* BTC `3BgSznxLB5u4WiuVERb1dKWeTqSSwK9NPW`
* BAT `0xaf25cdc7967213172a745453a64e8a0b59686729`
