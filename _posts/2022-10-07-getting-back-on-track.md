---
layout: post
title: "Getting back on track"
author: "Alison Harvey"
date: 2022-10-07
---
Two months into the project, I’m reviewing what I’d originally set out to do, and reflecting on progress so far. 

The main research focus for my project is Alma Digital – digital repository software I was responsible for implementing at Cardiff University. I had planned to use the project to investigate its potential to support academic needs. Can it support the creation of sustainable digital archives? Can it integrate with external tools to feed online exhibitions? 

Alma Digital uses IIIF (the International Image Interoperability Framework) to serve its images, but the software provider (Ex Libris) had made little of the advantages of this during our implementation phase. I also had yet to come across any fellow customers, anywhere in the world, that were making use of the functionality beyond their own installations. As an active member of the IIIF community for some years, I was keen to communicate the benefits and potential of IIIF to the Alma Digital community. 
<!--more--> 

Just prior to the commencement of the fellowship, I gave a presentation at WHELF 2022, to an audience of information professionals based in Welsh universities and research organisations. As a consortium, all WHELF members utilise Alma as their Library Management System, with the option - as we chose to pursue at Cardiff University - to adopt the Alma Digital module as an added extra.

I had very enthusiastic feedback from the presentation, which demonstrated the ways in which teaching and research could be enhanced through the IIIF support offered by Alma Digital. I was invited by Ex Libris to present similar content at their international conference in September, and my paper was accepted.

However, as I’ve documented in earlier posts, in the first few days of the fellowship, I discovered a problem. Ex Libris has updated their IIIF Presentation API from 2 to 3 since I’d delivered the WHELF presentation, and errors had appeared - all the IIIIF features and functionality I had demonstrated were no longer reproducible within Alma Digital. 

This had consequences for the presentation in September, and also for the pieces of practical work I’d hoped to complete in the first two months of the fellowship. I’d wanted to create some proof-of-concept digital archives and exhibitions that would pull Alma Digital content into third party platforms, but it was precisely this functionality that had been affected.

I could have responded to this by moving onto a different section of the project, but felt that my time would be more impactfully spent by raising awareness of the fault, developing short-term workarounds, and lobbying for a long-term fix. This is how I’ve spent the first two months:

-	trialling and testing behaviours to clarify the exact nature of the fault, and reporting it to Ex Libris via official channels
-	communicating the issue via worked examples on my GitHub blog to IIIF and Universal Viewer communities, seeking advice, and feeding back to Ex Libris
-	successfully trialling and testing alternative methods to pull content out of Alma Digital in the short-term
-	using these methods to rebuild existing digital projects
-	lobbying for the need for a long-term fix to the issue, using the platform of the Ex Libris conference to raise awareness among Ex Libris staff and customers of the range of features that could be restored.


The main barrier I’ve encountered is that Alma Digital appears to be working perfectly – within our own implementation. It’s only when trying to share content from our system with external tools using IIIF (the focus of my project) that errors become apparent. Raising awareness of IIIF and its potential was key to persuading Ex Libris that the issue was sufficiently impactful to develop a fix as a priority.

Since the presentation, I’ve been able to schedule a meeting with Alma Digital’s product owner, who has acknowledged and been supportive of the need for an imminent fix, and am due to meet with their developers later this month to take a look at the issue.

While part of me feels that I haven’t produced as much in the way of tangible digital outputs as I’d hoped, I think my tenacity in pursuing a solution has paid off, not just for our benefit but for all Alma Digital customers, and I hope to be able to resume work on some pilot digital resources once a fix is implemented. I then intend to write up findings as part of the final project report.

Still being uncertain of the timescale for a fix, I plan to turn my attention in the meantime to one of the other fellowship aims, which is to research and develop some introductory digital humanities training. I’ve been asked to prepare sessions on digital history and archives suitable for postgraduate students in our School of History, Religion and Archaeology later this month, so this seems like a good place to start.

I intend to discuss the realities of digitisation in the context of our activity at Cardiff – the realities and logistics – with the aim of conveying the huge resource implications. I hope this awareness will help students realise that digital archives represent a tiny proportion of the sources that are available to them, the decision-making processes that go into identifying what is digitised and how, and the implications these have for them as users of the archives. 
