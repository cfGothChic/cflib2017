---
layout: udf
title:  GetJulianDay
date:   2001-09-04T15:47:07.000Z
library: DateLib
argString: "[TheDate]"
author: Beau A.C. Harbin
authorEmail: bharbin@activematter.com
version: 1
cfVersion: CF5
shortDescription: Calculates the Julian Day for any date in the Gregorian calendar.
tagBased: false
description: |
 This function calculates the Julian Day for any date in the Gregorian calendar.  Astronomers have used the Julian period to assign a unique number to every day since 1 January 4713 B.C.E.  Julian Days begin at noon on the date specified.

returnValue: Returns a numeric value.

example: |
 <CFOUTPUT>Today's Julian Day is: #GetJulianDay()#</CFOUTPUT>

args:
 - name: TheDate
   desc: Date you want to return the Julian day for.
   req: false


javaDoc: |
 /**
  * Calculates the Julian Day for any date in the Gregorian calendar.
  * 
  * @param TheDate      Date you want to return the Julian day for. 
  * @return Returns a numeric value. 
  * @author Beau A.C. Harbin (bharbin@figleaf.com) 
  * @version 1, September 4, 2001 
  */

code: |
 function GetJulianDay(){
         var date = Now();    
     var year = 0;
     var month = 0;
     var day = 0;
     var hour = 0;
     var minute = 0;
     var second = 0;
     var a = 0;
     var y = 0;
     var m = 0;
     var JulianDay =0;
         if(ArrayLen(Arguments)) 
           date = Arguments[1];    
     // The Julian Day begins at noon so in order to calculate the date properly, one must subtract 12 hours
     date = DateAdd("h", -12, date);
     year = DatePart("yyyy", date);
     month = DatePart("m", date);
     day = DatePart("d", date);
     hour = DatePart("h", date);
     minute = DatePart("n", date);
     second = DatePart("s", date);
     
     a = (14-month) \ 12;
     y = (year+4800) - a;
     m = (month + (12*a)) - 3;
     
     JD = (day + ((153*m+2) \ 5) + (y*365) + (y \ 4) - (y \ 100) + (y \ 400)) - 32045;
     JDTime = NumberFormat(CreateTime(hour, minute, second), ".99999999");
     
     JulianDay = JD + JDTime;
     
     return JulianDay;
 }

oldId: 243
---

