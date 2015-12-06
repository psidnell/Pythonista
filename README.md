# Pythonista Utilities

Various iOS Pythonista Integrations I use.

Some of these need to be launched with the WorkFlow app via Action Extensions,
so for example you can export a map pin to a WorkFlow extension and have it launch the correct
Pythonista script with the pin data as an argument. Pythonista then processes that and can launch
other apps in turn.

## Useful links:

All this was developed entirely on an iPad, including managing this git repository with:

- [Pythonista](http://omz-software.com/pythonista/) - a full iOS Python dev environment.
- [Launch Center Pro](http://contrast.co/launch-center-pro/) - A useful launcher for Pythonista scripts.
- [WorkFlow](https://workflow.is) - an iOS automation utility. Another launcher but also much more.
- [Working Copy](http://workingcopyapp.com) - an iOS git/GitHub client.
- [Pythonista URL schemes](http://omz-software.com/pythonista/docs/ios/urlscheme.html).
- [WorkFlow URL Schemes](https://workflow.is/developer).

## Sending Apple Maps pins to Google, TomTom, Waze, OpenStreetmap, Omnifocus

In iOS9 Apple changed the Maps export format to a URL and "broke" my location based workflows. I've recreated them here with the help of Pythonista which is a big improvement on the pure WorkFlow scripts I used to have which were getting unwieldy.

These scripts require a WorkFlow Action Extension to forward the url exported by Apple Maps, here is an example of one:

![](LocationToOmnifocus_1.png)

![](LocationToOmnifocus_2.png)

The specific python scripts (named LocationTo...) then process the link and open the required app on the location.

Note that one exception is Here2OF.py which stores the current location as a nicely formatted OmniFocus note with title, address and links. This requires no input since it uses the current location. Thus it can be launched directly without the need for any argument. 

## WorkFlow for Importing Python scripts from DropBox

This WorkFlow lets the user choose a script from DropBox, stores the file content on the clipboard then opens the Pythonista script with the filename as an argument.

![](DropboxToPythonista.png)

Import.py uses the passed filename and clipboard to save the file in Pythonista.

As a safety measure it puts "IMPORTED_" on the front of the saved file so you don't accidentally overwrite anything important. It could check for the existence of the file first and just append a numeric suffix if it it already exists. Maybe later...

