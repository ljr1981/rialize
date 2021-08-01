# Rialize Progress!

## Overview
As a programmer, I want to know how many hours each day I worked on a particular project, but I don't want to have to punch a clock each time I start working (or stop the clock when I stop working). Moreover, I might forget to start the clock and stop the clock. Either way—I don't want to be bothered. Rialize helps me realize this goal by doing the monitoring for me! All I have to do is ensure Rialize is started (it will stop itself at the end of the day).

Rialize measures file-touches within a folder every 10 minutes across a day. Rialize assumes that 'file-touched' equals 'work done' within each quarter hour of time. When this 'touch data' is consolidated at the end of the day, Rialize will generate a report summarizing which hours had 'work done' on `files touched'.

Here is a sample Progress Report just generated by Rialize for the work I did on it yesterday.

```
Daily Progress Report
=====================

Date: 07/30/2021
Hours: 4.75 (Qtr-hours: 19)

+-----------------------------------------------------------------------------------------------------------------------+
|Max @ 4.79 per Touch
|-                                        XX  XX  XX                                                          
|-                                        XX  XX  XX                                                          
|-                                        XX  XX  XX                              XX                          
|-                                        XX  XX  XX                              XX                          
|-                                    XX  XX  XX  XX      XX                      XX                          
|-                                    XX  XX  XX  XX      XX                      XX                          
|-                                    XX  XX  XX  XX  XX  XX                      XX                          
|-                                    XX  XX  XX  XX  XX  XX                      XX                          
|-                                    XX  XX  XX  XX  XX  XX          XX      XX  XX                          
|-                                    XX  XX  XX  XX  XX  XX          XX      XX  XX                    
|min      00  01  02  03  04  05  06  07  08  09  10  11  12  01  02  03  04  05  06  07  08  09  10  11  AM/PM/
|        Mid                                              12  13  14  15  16  17  18  19  20  21  22  23  24-hour
+-----------------------------------------------------------------------------------------------------------------------+

Git Log
=====================
commit 2c242107c40efddf01501a493fdd4de150dfa5d8
Author: Larry Rix <ljr1981@msn.com>
Date:   Fri Jul 30 11:46:42 2021 -0400

    v0.0.0.10 restored the UTF-8 based chart template, but still needs
    to record the output progress report file as a UTF-8 file rather than just ASC-II.

commit 0c4d080fd527eec4a5ac0cb4f80d2cbb2cb032e6
Author: Larry Rix <ljr1981@msn.com>
Date:   Fri Jul 30 09:36:51 2021 -0400

    We have a working Progress Report Chart!

commit 2e41731c4adfcc7c7b50cc3d15053c336af532a7
Author: Larry Rix <ljr1981@msn.com>
Date:   Fri Jul 30 07:00:41 2021 -0400

    Progress report now has a primitive touch-count chart.
    Also removed older obsolete progress report txt files. Updated to
    v0.0.0.9 and generated new exe.

commit 3c9d4015d6557bd50efbfc973bf60c294159aabd
Author: Larry Rix <ljr1981@msn.com>
Date:   Thu Jul 29 18:53:29 2021 -0400

    updates for watch_list and new exe based on it

commit 2550d729c75aa99ebdcf756c8296f3b82f4e29b7
Author: Larry Rix <ljr1981@msn.com>
Date:   Thu Jul 29 17:59:48 2021 -0400

    Removal of quite a few magic numbers

commit c61e9dcea7ba9c25ac1bd852542b34b8c254ade6
Author: Larry Rix <ljr1981@msn.com>
Date:   Thu Jul 29 15:54:36 2021 -0400

    v0.0.0.7 corrections for UTC v Local times, plus better calc of sleep-cycles
    and other needed changes.

```

## Quick Reference
Install Rialize with the 'rialize_setup.exe' (see this repo). This is a Windows-based application only.

Once installed, be sure to add Rialize to your %PATH%. You may now open your favorite command line DOS prompt, navigate to the folder you would like to monitor, create a .\db\ folder in that directory, and then launch Rialize with the following command line call:

   rialize --rtm --text .\

This will initialize Rialize, whereupon it will generate its first touch-file in the \db\ folder and then start waiting for each 10 minute segment. After each 10 minute pause, it will generate another touch-file. This will continue until midnight of the day you start Rialize.

    Let's say File-A is touched at 10:37 AM and again at 2:15 PM and then again at 2:17 PM — Rialize 
    will tell me that I've done 30 minutes of work on that "project" that day (the 2:15 and 2:17 only 
    count as a single 15 minutes of work).
    
    So even if I were staring at code for the four hours between those touches, we don't count that 
    as work because no updates were saved to disk during that time span.

The next day, you can run the following command line call and produce a Progress Report:

    rialize --report --text .\

This will produce a Progress_report_[stamp].txt file like the example above.

## Future Work
Rialize is going places. Here is the roadmap ahead:
- The next step is to test the multi-project facilities of Rialize—that is—can Rialize perform as-expected using the '--file' option rather than the '--text' (single project) option?
- Assess any feedback for improvements to the Daily Progress Report. This may entail a Linux-based product as well as facilities beyond a reliance on GitHub repositories.
- Provide first linkage to Foggler BDD specifications, whereby Rialize Progress Reports can speak to the question: "How much more work is there to be done?" (in terms of BDD spec completion).

That last item is very non-trivial. It depends on Foggler being more mature and a serious think-about regarding how one measure future work rather than just daily work done as meaure by file touch recording.

## Version Info
- v0.0.0.13 — Improved watch list using Regex instead of an earlier hack.
- v0.0.0.12 — Using just ASC-II for the chart because all attempts (so far) at UTF-8 or Unicode solutions have failed.
- v0.0.0.11 — Reverted UC_UTF8_STRING back to STRING_32. The chart is still not readable, so I need to come up with another solution.
- v0.0.0.10 — The report generator now knows how to make a basic touch-point chart showing a timescale with the touch-counts/hour from Midnight-to-Midnight same-day.
- v0.0.0.8 — Lots of changes including bug fix where Rialize was not reporting touched files in a reasonable way. It now reports only files changed in last 10 minutes with each cycle through looking for changes.
- v0.0.0.3 — Missing correct version and corrects a bug where Rialize was reporting touches on its own files as work against the overall project folder, which is (of course) not true.
- v0.0.0.2 — Updated to create its own \db\ project subfolder as-needed. Previously, it was crashing and the user needed to create the subfolder.
- v0.0.0.1 — First initial commit of the Rialize installer.
