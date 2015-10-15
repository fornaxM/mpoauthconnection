# Introduction #

MPOAuthMobile is a sample application showing how to link and use MPOAuth with your iPhone or iPod Touch application. It differs from MPOAuthClient since it's not really useful as a diagnostic tool since text input on the iPhone is nowhere near as easy as on a desktop. Instead it utilizes the MPOAuthAPI delegate API to manually take part in the automatic authorization to prevent the default launch of an external browser to handle requesting user access credentials.

# Using MPOAuthMobile #

There's not much to do in this case. All you need to do is launch the application and watch it do everything for you except login. That you still have to do for yourself.

# How MPOAuthMobile is built #
On the iPhone there are no frameworks or external libraries allowed, as [Apple](http://apple.com) wants you to deliver your app as one executable file. Rather than producing a specially made static library for iPhone users to link in, I opted instead to just require iPhone users to compile the library into their application directly. The MPOAuthMobile sample application already does this, just including all the source files and compiling them directly into the mobile application.