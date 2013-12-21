beet-dates
==========

plugin for beets that lets you search for musicfiles added between certain dates

 this plugin - for the lovely beets - 
 lets you do a search on the tag: added.
 
 Like this added:=yesterday
           added:="yesterday morning"
           added:= "last night"
           added:="2012"
           added:="2012/10.."
           added:="..prev 5 weeks"
           
 it uses the prefix '='
 you need the dateslib.py and the dates.py
 put them both in your plugin folder
 add dates to your plugin list in your beets/config.yaml
 and you're ready to go  
 
 
 The search can be verbal or numeric.
 
 a verbal search is ex: this afternoon, yesterday, last night, 
    this week, last 2 months, prev year, last year, this year,
    prev 5 month..yesterday night, this morning.. prev 2 minutes
 a numeric search is ex: 2012.10.(returns the whole 10th month)
    2012..2013.02(start of 2012 upto 2013.03.01 00:00:00)

 You can combine verbal and numeric searches
     ex: 2012..last night
 
 verbal searches can have 3 parts
 of which the second part can be a number
 the first part can be :
    this: ex.. this year, month, week, day, hour, minute,
          morning, afternoon, evening, night
    last: returns the last year, month,week... till now.
          So now is the end and count back a year, month...
          if today is friday than last week is last friday to now
    prev: if today is friday than the prev week is ending last sunday
          and beginning sunday a week further back 
 and then there are these special words: yesterday, today

 if you got whitespaces between words
 you should use " or ' at the beginning and end
    added:="last 5 minutes"
 
 for numeric requests: 2012/10/12/23/59 (Y,m,d,H,mi)
    is the input format.
    when you give just a part of this, it gets that:
        2012 gives you all of 2012
        2012/10/01 gives you everything from the 10/1
    if you put in a '=' , you copy the number from 'now'
        so 2012==== copies the values from today after the 2012. 
    if you put in a 'x', you set that value to zero
         2012:10xxxx (its okay to give more xxxx or =====, gets cut off)
         is 2012/10/01/00:00
    You can not do 20121001, we need something between the numbers
        ,;:/ are all okay
    spaces or not before after '..' ... all ok


 You can use this with your smartplaylistplugin:
    query: 'added:="last hour"'(watch the ' and ")
    name: 'addedlasthour.m3u'                                                                                                                                          
    query: 'added:="prev month"'
    query: 'added:=today"
    
    the smartlist stays the same untill you update your datebase then
    the content of these smartlists get changes....
