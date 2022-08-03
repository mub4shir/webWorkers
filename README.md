# Service Workers & Offline Course by Kyle Simpson

Code for the Web Workers section of the Service Workers and Offline course by Kyle Simpson.

## Starter Exercise Files

To get started, download the [Starter Files (ZIP)](https://static.frontendmasters.com/resources/2019-05-10-service-worker-pwa/service-workers-starter.zip)

Don't forget to `npm install` the necessary modules.



````
    # speaking of the data that we're gonna be sending between workers and 
    out web page, the data is copied. It is not send by refrence, if it was send by refrence we would
    have all kinds of threaded issues to bt concerned about. so the data is copied 
    now normal data like numbers and strings are all already obviously copied,
    but even if u send something like a JSON object, that entire object is going to be copied 
    and it's copied by the way of what's called structured clone algorithm.
    which is part of the web specfication.
    
    
    # for a while this was okay and then people started saying well web workers aren't useful, because not only is that inefficient from a memory 
    perespective, but that also is very inefficient from a processing perspective. The whole point of a web worker is to be off thread and better 
    and if i have to make a copy of my 100 megabytes of data, that's no good.
    So they had for a while, a thing called transferable, whaich was a way of basically creating 
    a special kind of, like a array that you put some data onto it and and as soon as you posted it to a web worker, it went away from the web page
    They literally deleted it from the web page. And put it without copying, into the worker thread and then vice versam, 
    as soon as you posted it from a worker thread back to page, it went away from the worker and put it back.
    So there's only ever one copy of that thing in any given place, but it's never in both places at once.
    That seemed like an intresting and cool idea, as far as I' m aware, I mean they shipped that, but that's been kinda deprecated
    it seems like they went away from transferables so that doesn't seem like something that's got, much of a future 
    
    
    
    # They(web platfrom / javascript) shipped a feature called shared array buffers and it was basically like the V2 of transferables.
     So it was a literal shared memory segment that could be accessed at the same time from two different threads of javascript, which is a recipe for chaos.
     But they also shipped another API on top of it, called atomics, whcih would allow you to do new texas or semi fours or some other kindof blocking remotely 
     so that only one of that threads was accessing the data, the shared memory data at that piont, the idea was we're just gonna stuff 
     in a shared memory segment. Shipt it off to a worker and then let it work on it and then let it tell us when it's done.   
     So we'll just pull it back out of the same shared array memory. That sounds all well and good until about a year and a half ago  
     You might remember the CPU craziness that happened with the chips, I think it was called specter or something like that, that came out 
     and it was like being able to read people's  private information out of memory or out of the process of RAM or something 
     a vulnerability in the way processors worked and they were able to read this memory 
     Well it turned out that, that was in part being explioted on web pages. because the way that bug was exploited required what's called a 
     high resolution timer meaning a timer that has down to like nanosecond precision that how those attack vectors generally work 
     and so we are actually very carefull don't ship anything in the web platform that can give a high resolution timer, because then people are gonna exploit it.
     Well, it turns out shared array buffers are perfect way of implementing high precision timming.
     And that's exactly what they did, is they exploited that feature. 
     Every time they give us something cool, some jerk goes and abuses it and that's why we can't have nice things 
     So , the point is right now what you can rely upon cross browser is that you can send stuff copying string and thins,
     so do be aware that if you're going to send a bunch of data 
     
     
      
     
   
````
