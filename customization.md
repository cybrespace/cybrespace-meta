# Customizing your Mastodon Instance

After modifying any of the following files, you'll need to run the following
command:

    RAILS_ENV=production bundle exec rails assets:precompile

## Colors

As of 1.1 you can change colors in your custom.scss:

    app/assets/stylesheets/custom.scss 

There are four colors you can change.

    $color1: #282c37; // darkest
    $color2: #d9e1e8; // lightest
    $color3: #9baec8; // lighter
    $color4: #2b90d9; // vibrant

$color1 controls background colors, like the backdrop and the column panel
backgrounds.

$color2 and $color3 control text shades on about pages, soft highlight colors,
glows, and tints.

$color4 controls bright/saturated elements, like the TOOT! button and other
interactable buttons.

I would recommend customizing the colors by mainly changing the hue; the
saturation and value/lightness are fairly important to maintaining good
readability and human factors.

## Images

Most of the image assets are in the following folder:

    app/assets/images/

Here are some you may be interested in modifying:

 - `background-photo.jpeg` -- the background of the about pages (`/about` and
   `/about/more`) as well as any static-view pages like people's profiles and
    post detail views accessed from other instances

 - `fluffy-elephant-friend.png` -- the fluffy elephant friend on the new user
   landing page

 - `logo.png` -- the Mastodon logo displayed at the top of the landing page and
   other about pages

## About page text

Here are some relevant files to look at / edit:

 - `app/views/about/index.html.haml` -- the landing page template. This is where
   you could change the big text at the top to the name of your instance instead
    of "Mastodon"

 - `config/locales/en.yml` -- the `about_mastodon' section is the paragraph
   under the heading above (replace 'en' with your language of choice)

 - `app/views/about/terms.en.html.haml` -- the terms and conditions for your
   instance

 - Administrator control panel, Site Settings section, extended site description
   -- the text shown on the "About this instance" page


## UI text

If you want to customize UI verbs like "favourite", "post", "Toot!", etc, here's
where to look:

 - `app/assets/javascripts/components/locales/en.jsx` -- this is where the Toot!
   button text is defined among other things

 - `config/locales/en.yml`

 - `config/locales/simple_form.en.yml`

 - `app/assets/javascripts/components/features/...` -- files in here contain
   most of the miscellaneous UI strings that need text-replacement to insert
    e.g. user names. For example:

 - `app/assets/javascripts/components/features/notifications/components/notification.jsx` -- the "Alice favourited/boosted your status" messages

 - `app/assets/javascripts/components/features/getting_started/index.jsx` -- the
   Getting Started panel tab names

## UI icons

These are all over the damn place. You'll want to grep for "icon:", "icon=",
"fa-", etc, as well as the name of the icon you want to replace in the
[http://fontawesome.io/icons/](fontawesome) set. Some likely candidates, depending on what
you're doing:

 - `app/assets/javascripts/components/features/notifications/components/notification.jsx` -- fav/boost icons in notifications

 - `app/assets/javascripts/components/features/status/components/action_bar.jsx`and `app/assets/javascripts/components/components/status_action_bar.jsx` -- fav/boost icons on toots

 - `app/assets/javascripts/components/features/getting_started/index.jsx` -- getting started panel icons

## Incorporating the variable-width column userstyle:

Add the following lines to `app/assets/stylesheets/custom.scss`:

   @media screen and (min-width: 1300px) {
      .column {
        flex-grow: 1 !important;
        max-height:100vh;
      }

      .drawer {
        width: 20%;
      }
  }
