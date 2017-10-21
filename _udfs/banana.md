---
layout: udf
title:  Banana
date:   2017-09-10 16:26:53 -0500
library: StrLib
argString: x,y
author: Raymond Camden
authorEmail: raymondcamden@gmail.com
version: 2
cfVersion: CF6
shortDescription: I make Bananas
description: |
 This returns a banana

returnValue: Returns a string.

example: |
 <cfscript>
 x = 1;
 abort("Foo");
 </cfscript>

args:
 - name: foo
   desc: fooball
   req: true

javaDoc: |
 /*
  Capitalizes the first letter in each word.
  Made udf use strlen, rkc 3/12/02
  v2 by Sean Corfield.
  v3 by Chris Jordan
 
  @param string 	 String to be modified. (Required)
  @return Returns a string. 
  @author Raymond Camden (ray@camdenfamily.com) 
  @version 3, March 9, 2007 
 */

code: |
 function date2ExcelDate(dateString) {
   var rtrnString = '';
   if(isDate(dateString)) {
     return dateDiff("d", createDate( 1899,12,30 ), dateString);
   };

   return rtrnString;
 };

---
