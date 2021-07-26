First of all, no i didn't work on this all day solid. 

So here's a bit of a report: 

## webcomponents
* video I watched: https://www.youtube.com/watch?v=xIYOyiAE-sYquick
* video notes: https://github.com/ogrotten/super-train/blob/master/webcomponent-setup.mdtest
* my test source: https://github.com/ogrotten/svelte-quiz

Following the vid, I created a webcomponent using svelte. I started with the Quiz app from levelup. To test I did this in the above "test source"

1. npm run dev on the svelte app
2. created and launched a separate simple HTML page
3. that page only called the bundle.js and then called the custom tag for the webcomponent. 

The end result is that the stand alone page showed, as a component only, the quiz. 
source of the calling html file: https://github.com/ogrotten/svelte-quiz/blob/conversion/index.html

## inboxsdk

I started with the previous repo, and attempted to call that app from inboxsdk... which only uses HTML methods to inject html source.

Without going into all the details, the end result: CORS. If you know how to deal with CORS in a svelte app, it may be worth looking at beyond this, but as far as I was concerned at the moment CORS was the showstopper.

## svelte + inboxsdk
* article: https://dev.to/khangnd/build-a-browser-extension-with-svelte-3135
* repo: https://github.com/khang-nd/browser-extension-svelte
* my repo: https://github.com/ogrotten/super-train

The article is short and makes a lot of sense. Getting the "app" into an extension was pretty quick. 

Taking the next step to add inboxsdk was not as simple as adding it to public/index.html. The  console on gmail reports "inboxsdk.js cannot be found". Based on other reading, I'm sure that it has to be loaded in the rollup config.

### other articles
* angular, inboxsdk, webpack: https://groups.google.com/g/inboxsdk/c/Hj07DdQe2IM?pli=1
* vue + inboxsdk: https://dev.to/mikeeus/building-gmailchrome-extension-with-vuejs-and-inboxsdk-20ah