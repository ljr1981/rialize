# Rialize Progress!

## Overview
Rialize is a command-line program that periodically monitors file touches (access, change, modify) within a root folder. Every 10 minute, it will look to see if any file has been touched and make a record of that touch in a .\db\ folder as a *.json file. Rialize can be told to run until midnight of the current day, whereupon it will stop. The next day, you can tell Rialize to look at yesterdays data collection and build a Progress Report with some basic information about hours worked.

Here is a sample Progress Report just generated by Rialize for the work I did on it yesterday.

    Daily Progress Report
    =====================
    
    Date: 07/25/2021
    Hours: 6.25 (Qtr-hours: 25)
    
    Git Log
    =====================
    commit efb8a4648e6750a3e682837f8718a323178dc3eb
    Author: Larry Rix <ljr1981@msn.com>
    Date:   Sun Jul 25 10:22:20 2021 -0400
    
    new exe and installer as well as handling getting the right
    directory established when running from the C:\programs etc

    commit 305614357ac13307e32858edccf76d59c7e4404e
    Author: Larry Rix <ljr1981@msn.com>
    Date:   Sun Jul 25 08:56:13 2021 -0400
    
        test tweaks

## Quick Reference
Install Rialize with the 'rialize_setup.exe' (see this repo). This is a Windows-based application only.

Once installed, be sure to add Rialize to your %PATH%. You may now open your favorite command line DOS prompt, navigate to the folder you would like to monitor, create a .\db\ folder in that directory, and then launch Rialize with the following command line call:

   rialize --rtm --text .\

This will initialize Rialize, whereupon it will generate its first touch-file in the \db\ folder and then start waiting for each 10 minute segment. After each 10 minute pause, it will generate another touch-file. This will continue until midnight of the day you start Rialize.

NOTE: Let's say File-A is touched at 10:37 AM and again at 2:15 PM and then again at 2:17 PM — Rialize will tell me that I've done 30 minutes of work on that "project" that day (the 2:15 and 2:17 only count as a single 15 minutes of work).

The next day, you can run the following command line call and produce a Progress Report:

    rialize --report --text .\

This will produce a Progress_report_[stamp].txt file like the example above.
