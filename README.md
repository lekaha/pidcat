PID Cat
=======

An update to Jeff Sharkey's excellent [logcat color script][1] which only shows
log entries for processes from a specific application package.

During application development you often want to only display log messages
coming from your app. Unfortunately, because the process ID changes every time
you deploy to the phone it becomes a challenge to grep for the right thing.

This script solves that problem by filtering by application package. Supply the
target package as the sole argument to the python script and enjoy a more
convenient development process.

    pidcat com.oprah.bees.android


Here is an example of the output when running for the Google Plus app:

![Example screen](screen.png)


Install
-------

Get the script:

 *  OS X: Use [Homebrew][2].

         brew install pidcat

 * Others: Download the `pidcat.py` and place it on your PATH.


Make sure that `adb` from the [Android SDK][3] is on your PATH. This script will
not work unless this is that case. That means, when you type `adb` and press
enter into your terminal something actually happens.

To include `adb` and other android tools on your path:

    export PATH=$PATH:<path to Android SDK>/platform-tools
    export PATH=$PATH:<path to Android SDK>/tools

Include these lines in your `.bashrc` or `.zshrc`.


Usage
-----

usage: pidcat.py [-h] [-w N] [-l {V,D,I,W,E,F}] [--color-gc]
                 [--always-display-tags] [-s DEVICE_SERIAL] [-d] [-e] [-c]
                 [-t]
                 [package [package ...]]

Filter logcat by package name

positional arguments:
  package               Application package name(s)

optional arguments:
  -h, --help            show this help message and exit
  -w N, --tag-width N   Width of log tag
  -l {V,D,I,W,E,F}, --min-level {V,D,I,W,E,F}
                        Minimum level to be displayed
  --color-gc            Color garbage collection
  --always-display-tags
                        Always display the tag name
  -s DEVICE_SERIAL, --serial DEVICE_SERIAL
                        Device serial number (adb -s option)
  -d, --device          Use first device for log input (adb -d option).
  -e, --emulator        Use first emulator for log input (adb -e option).
  -c, --clear           Clear the entire log before running.
  -t, --time            Use time format for logcat (logcat -v time)


 [1]: http://jsharkey.org/blog/2009/04/22/modifying-the-android-logcat-stream-for-full-color-debugging/
 [2]: http://brew.sh
 [3]: http://developer.android.com/sdk/
