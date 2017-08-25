# Touchscreen
CSS and JavaScript for the CTL's touchscreen directory

The normal version of the staff directory is [here](http://ctl.yale.edu/our-staff) and the touchscreen version is [here](http://ctl.yale.edu/touchscreen/our-staff).

### Disclaimer
Because the CTL site uses a custom template this might not work for you.

## Background
The CTL touchscreen directory looks like a custom app, but it's actually just the [CTL Site](http://ctl.yale.edu/)'s (Drupal 7) user directory, with custom views, CSS, and JavaScript (JQuery).
This is being displayed using [Rise Vision](https://www.risevision.com/)'s split display view on the giant touchscreen in our lobby at 301 York Street.

## Touchscreen Hardware and Software Specs
Here are the hardware and software specs:
- Screen is an 80" Multi-touch Screen Professional Display from Panasonic [TH-80BF1U](http://business.panasonic.com/TH-80BF1U.html#prefn1=disp_screen_size&prefv1=80%22&nextIndex=0&start=1&cgid=products-avtechnology-professionaldisplays-led\)
- Behind it is an Intel NUC running Windows
- The display software is [Rise Vision](https://www.risevision.com/)

## Included Files
The two files included are the CSS to make the directory look pretty, and the JavaScript for the accessibility button.

### touchscreen.css
This CSS makes the user images display nicely in a grid, and puts the user names overlaid on the images (I used a custom image style to add the shadow overlay). It also makes the filter buttons appear on the left side and styles them to match the site. It also hides everything from the site we don't need (like the header and footer) and disables external links from profiles.
I added this custom CSS to the site using [CSS Injector](https://www.drupal.org/project/css_injector).
Because of the wonkyness of Drupal's CSS and my inability to edit the actual template files, I had to include a few `!important` rules to override some of the template's CSS. So be careful that it doesn't overwrite anything important and use this at your own discretion! I recommend selecting "Add on only the listed pages" in CSS injector and specifying only the touchscreen directory pages.

### accessibility.js
According to [ADA Design Guidelines](https://kiosk.com/sites/kiosk.com/files/ada_design_guidelines_brochure.pdf), the maximum height of interactive touchpoints should not exceed 48". Because some touchpoints are above this height, I created this button to slide all the content to below 48".
This file contains the JQuery for the accessibility button. I added it using [JS Injector](https://www.drupal.org/project/js_injector).
I have a block on the touchscreen page that contains the button:
```
<button><img alt="accessible view" id="accessibilitybutton" src="/sites/default/files/images/accessible.jpg" style="width: 100px; height: 100px; padding: 3px 0px;" /></button>
```

### people_view_export
This is the code exported from our people view.

## Tips
- On the Drupal site, [X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options) need to be changed to allow for iframing.
- The display probably won't look the same on your computer as it will on the large display, even when using the [Emulated Devices](https://developers.google.com/web/tools/chrome-devtools/device-mode/) tool in Chrome, so be sure to design with this in mind.
- I also added a back button on the profile pages as a block: `<a href="http://ctl.yale.edu/touchscreen/our-staff"><button id="edit-reset">&#60; Back</button></a>`.
