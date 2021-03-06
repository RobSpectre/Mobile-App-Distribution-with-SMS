# Mobile App Distribution with SMS 

An example Flask application demonstrating how to invite users to download your
mobile application using Twilio SMS.

Built for Rob's talk on mobile app distribution originally given at USV, June
2012.

[![Build
Status](https://secure.travis-ci.org/RobSpectre/Mobile-App-Distribution-with-SMS.png?branch=master)](http://travis-ci.org/RobSpectre/Mobile-App-Distribution-with-SMS)

## Summary

This is a quick Flask app I put together to demonstrate a common Twilio use
case - using SMS to invite users to download your mobile application.  A
powerful implementation that require little time and is supercheap, leveraging
Twilio SMS on your webpage is an easy way for you to bridge the distance between
your users' keyboards and their phones and get them in their phone's App Store
to install your app right away.

It works like this:

1. A user inputs his/her phone number in a simple web form.
1. Using Twilio SMS, you send him/her an invitation link to install your app.
1. When the user clicks on the link in the text message, he/she is redirected to
   the native App Store for his/her phone.
1. Your user installs the app - with *crazy* conversion rates!

For more information on how to use Twilio to drive users to your mobile app,
check out [my talk on the
subject](https://github.com/RobSpectre/Talks/tree/master/Mobile%20App%20Distribution%20via%20SMS)
or a little whitepaper we whipped up on
[the Twilio website](http://www.twilio.com/solutions/mobile-app-distribution).

The app used in this example is for my favorite mobile game, [Plants vs.
Zombies](http://www.popcap.com/games/plants-vs-zombies/pc).


## Features

This example app comes loaded with the kind of tasty goodness you expect from
Twilio, including:

* _Production Ready Form_ - ready-to-use Python web form with basic phone number
  validation.
* _Invitation Link_ - Code to redirect your users to their native app stores.
* _Easy Deployment_ - Use Heroku to see this use case in action in *seven*
  commands.
* _Full Test Suite_ - Seriously.  It's good for you.


## Usage

Once you deploy this app, you get a simple web form that asks you to put in your
phone number:

![Invitation web 
form](https://raw.github.com/RobSpectre/Mobile-App-Distribution-with-SMS/master/static/images/screenshot0.png)

Then presto, the user receives a text message with a magical link!

![Message the user
receives](https://raw.github.com/RobSpectre/Mobile-App-Distribution-with-SMS/master/static/images/screenshot1.png)

Then - holy biscuits! - regardless of what type of phone they are using, they
get redirected *right* to their native app store to install!

![Holy crap I'm in the
app store](https://raw.github.com/RobSpectre/Mobile-App-Distribution-with-SMS/master/static/images/screenshot2.png)

Or just text anything to (646) 666-9422 on both an iOS and an Android device to see it
without installing anything at all.


## Installation

Step-by-step on how to deploy and develop this app.

### Deploy 

1) Grab latest source
<pre>
git clone git://github.com/RobSpectre/Mobile-App-Distribution-with-SMS.git 
</pre>

2) Install dependencies
<pre>
make init
</pre>

3) Navigate to folder and create new Heroku Cedar app
<pre>
heroku create --stack cedar
</pre>

4) Deploy to Heroku
<pre>
git push heroku master
</pre>

5) Scale your dynos
<pre>
heroku scale web=1
</pre>

6) Configure Heroku to use your Twilio credentials.
<pre>
python configure.py --account_sid ACxxxxxx --auth_token yyyyyyy
</pre>

7) Open the app in your browser and get an invite!
<pre>
heroku open
</pre> 


### Development

Be sure to follow the configuration steps above and use this step-by-step
guide to tweak to your heart's content.

1) Install the dependencies.
<pre>
make init
</pre>

2) Launch local development webserver
<pre>
foreman start
</pre>

3) Open browser to [http://localhost:5000](http://localhost:5000).

4) Tweak away on `app.py`.


## Testing

This example app comes with a full testing suite with the same kind of form
validation that you would want to use in production.  To run the tests, simply
use `nose` with this shortcut command:

<pre>
make test
</pre>


## Anatomy

This app does have a little more complexity than our usual examples in an effort
to be production-ready.  Here's a quick rundown of all the important files:

* `local_settings.py` - Contains all the configuration options for the app,
  including Twilio credentials and the URIs you want to which you wish to direct
  your mobile users.
* `app.py` - The meat of the app.  Contains all the logic for rendering the
  form, sending the invites, and redirecting mobile users.
* `forms.py` - The Form along with some basic validators that make it suitable
  for production use.
* `tests` - Test suite testing the web, Twilio and form validation functionality
  of this example.
* `templates` - The gorgeous interface I surreptitiously from
  [Andres](http://twitter.com/enborra).
* `static` - Location of the styles for above.


## Meta 

* No warranty expressed or implied.  Software is as is. Diggity.
* [MIT License](http://www.opensource.org/licenses/mit-license.html)
* Lovingly crafted by [Twilio New
 York](http://www.meetup.com/Twilio/New-York-NY/) 

[![githalytics.com
alpha](https://cruel-carlota.pagodabox.com/9a41760e4b164083b1035a5a62f20d4f
"githalytics.com")](http://githalytics.com/RobSpectre/Mobile-App-Distribution-with-SMS)
