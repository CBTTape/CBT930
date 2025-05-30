# CBT930
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 930 is from Phil Polchinski and contains supporting JCL   *   FILE 930
//*           and other materials to use his CALENDAR FILE, which   *   FILE 930
//*           is found in EBCDIC format on File 932, and in zipped  *   FILE 930
//*           ASCII format on File 933.                             *   FILE 930
//*                                                                 *   FILE 930
//*           The calendar file presented here, can be generated    *   FILE 930
//*           in many date ranges, by Phil's program called         *   FILE 930
//*           CALFILE, but all that is really needed by anyone,     *   FILE 930
//*           is his "maximum size file" which contains all dates   *   FILE 930
//*           from the years 1753 thru 2600.                        *   FILE 930
//*                                                                 *   FILE 930
//*           The CALENDAR FILE has record length 35, and can be    *   FILE 930
//*           blocked.  Its size depends on the year ranges used    *   FILE 930
//*           when the CALFILE program is executed.                 *   FILE 930
//*                                                                 *   FILE 930
//*           In Files 932 and 933, we distribute a large-range     *   FILE 930
//*           calendar file, which ranges from years 1753 to 2600.  *   FILE 930
//*                                                                 *   FILE 930
//*           The format of this calendar file allows for           *   FILE 930
//*           sure-fire calculations (which are accurate) for       *   FILE 930
//*           complicated date-difference questions, and for all    *   FILE 930
//*           kinds of other purposes, all having to do with        *   FILE 930
//*           dates.                                                *   FILE 930
//*                                                                 *   FILE 930
//*           email:  philmpolchinski@hotmail.com                   *   FILE 930
//*                                                                 *   FILE 930
//*     Phil has now released load modules for his two programs:    *   FILE 930
//*                                                                 *   FILE 930
//*           CALFILE  -  program to produce the calendar file      *   FILE 930
//*                                                                 *   FILE 930
//*           CALPRINT -  program to print calendars from the       *   FILE 930
//*                       calendar file                             *   FILE 930
//*                                                                 *   FILE 930
//*        These two programs require a license key (supplied).     *   FILE 930
//*        See the note just below, as to why.                      *   FILE 930
//*                                                                 *   FILE 930
//*     Member CALREF is documentation in PDF format, which shows   *   FILE 930
//*     how to use CALFILE and CALPRINT.  See note just below.      *   FILE 930
//*                                                                 *   FILE 930
//*     ----------------------------------------------------------  *   FILE 930
//*                                                                 *   FILE 930
//*              * * * * * *  N O T E  * * * * * *                  *   FILE 930
//*                                                                 *   FILE 930
//*     Phil is retaining ownership of these two programs (but      *   FILE 930
//*     not ownership of the file format), and for this reason,     *   FILE 930
//*     I am making an exception to my rule of not allowing         *   FILE 930
//*     timeouts on any submissions to the CBT Tape.  In Phil's     *   FILE 930
//*     case, he is including a 75-YEAR LICENSE KEY for anybody     *   FILE 930
//*     to use his programs, included here as member KEYEBCDC.      *   FILE 930
//*     Since the key is for 75 years, which is a long time,        *   FILE 930
//*     I am making this exception.                                 *   FILE 930
//*                                                                 *   FILE 930
//*     Another reason why I am making an exception:                *   FILE 930
//*                                                                 *   FILE 930
//*     File 934 will contain a DFSORT job to produce the           *   FILE 930
//*     maximum-size file, which is not dependent on the CALFILE    *   FILE 930
//*     program and is therefore not dependent on a timeout.        *   FILE 930
//*     So the file is still reconstructible without a timeout      *   FILE 930
//*     and the system will not break.                              *   FILE 930
//*                                                                 *   FILE 930
//*     Of course the CALFILE program is more flexible to set up    *   FILE 930
//*     than the DFSORT job, and the CALFILE approach is much       *   FILE 930
//*     easier to use, and it is preferred.                         *   FILE 930
//*                                                                 *   FILE 930
//*              * * * * * *  N O T E  * * * * * *                  *   FILE 930
//*                                                                 *   FILE 930
//*     ----------------------------------------------------------  *   FILE 930
//*                                                                 *   FILE 930
//*     A reference manual to use this file and software, is        *   FILE 930
//*     found in member CALREF, which is a PDF format file.         *   FILE 930
//*                                                                 *   FILE 930
//*     The Calendar File itself can be found in Files 932 (EBCDIC) *   FILE 930
//*     and 933 (ASCII), and therefore it is not included here.     *   FILE 930
//*                                                                 *   FILE 930
//*     To obtain the calendar file more easily, File 932 contains  *   FILE 930
//*     an EBCDIC version of the calendar file (LRECL=35), and      *   FILE 930
//*     File 933 contains a zipped ASCII text version of the        *   FILE 930
//*     calendar file.  So you don't need the CALFILE program       *   FILE 930
//*     at all, unless space considerations dictate, in your        *   FILE 930
//*     case, that you have to generate the calendar file for       *   FILE 930
//*     a smaller date range, which would take up less space.       *   FILE 930
//*                                                                 *   FILE 930
//*     Sample problems which can be solved using this file:        *   FILE 930
//*     ------ --------                                             *   FILE 930
//*                                                                 *   FILE 930
//*     Create a list of dates containing all third Mondays         *   FILE 930
//*          that will occur during a 100 year period?              *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the number of Tuesdays that will occur during     *   FILE 930
//*          the month of January 2012?                             *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the calendar date for the last Tuesday during     *   FILE 930
//*          the month of January 2012?                             *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the exact interval between February 15 and        *   FILE 930
//*          May 15, 2011                                           *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the exact interval between February 15 and        *   FILE 930
//*          May 15, 2012                                           *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the new calendar date when adding 180 days to     *   FILE 930
//*          November 20, 2010                                      *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the new calendar date when adding 180 days to     *   FILE 930
//*          November 20, 2011?                                     *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the calendar date and day of the week for         *   FILE 930
//*           Julian Date 058" in the year 2012                     *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the Day of the Week for July 4, 2014              *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the calendar date for Thanksgiving Day, 2014      *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the calendar date for the Monday before           *   FILE 930
//*     Thanksgiving Day, 2014                                      *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the number of days remaining in the month,        *   FILE 930
//*          when it is February 19, 2011?                          *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the number of days remaining in the month,        *   FILE 930
//*          when it is February 19, 2012                           *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the number of days remaining in the               *   FILE 930
//*          year, when it is February 19, 2011?                    *   FILE 930
//*                                                                 *   FILE 930
//*     Determine the number of days remaining in the year,         *   FILE 930
//*          when it is February 19, 2012                           *   FILE 930
//*                                                                 *   FILE 930
//*     ------------------------------------------------------      *   FILE 930
//*                                                                 *   FILE 930
//*     Files 932 and 933 contain the maximum-size file which can   *   FILE 930
//*     be created with Phil Polchinski's program, so therefore     *   FILE 930
//*     you can program solutions to solve all the date problems    *   FILE 930
//*     which you want to solve (hopefully) between the years of    *   FILE 930
//*     1753 thru 2600.                                             *   FILE 930
//*                                                                 *   FILE 930
//*     Best of everything..........                                *   FILE 930
//*                                                                 *   FILE 930
```
