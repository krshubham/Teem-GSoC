# GSoC'17 summary: Third party integrations and extension of some features, Teem
### Kumar Shubham |  [website](http://krshubham.github.io/) | [twitter](https://twitter.com/krshubham1708) | [github](https://github.com/krshubham) | [email](mailto:kumarshubham347@gmail.com)

## Introduction

I'd like to first start by thanking my mentor [Antonio](https://github.com/atfornes), who was so friendly that I never felt like I was talking to someone who is senior to me. Whatever I have done wouldn't have been possible without our daily meetings, which were scheduled to be for 5 minutes but often we discussed things for more than 30 minutes! After working this summer I can say that I have got a good knowledge of how things go in a large codebase and how we should contribute in open source projects! I also got to know some quite details about javascript and also got to work with docker!. In short, it was a wonderful experience!

*I also made a presentation that will give you a slight introduction to what things I did during this summer at Berkman Klein Center, Harvard University under Google Summer of Code! [Here](https://prezi.com/p/ehecqd0ulggn/) is the prezi!*

*Below is a summary of the work that I did during this summer 2017*

## The goal of the summer 2017
When I was drafting my proposal for Teem, the one thing on my mind was:

> Internet applications do not exist as independent islands but rather as a part of a live ecosystem where everything is connected.

This was the major thought which helped me in shaping my proposal. Thus with this and also keeping in mind the things that were to be implemented in Teem I decided to go over these three things in my proposal:

+ [Contextual link previews](https://gist.github.com/krshubham/f8a6024d37c8e50f157ae5f745ebfdaa#contextual-link-previews)
+ [Better SEO indexing of Teem webpages](https://gist.github.com/krshubham/f8a6024d37c8e50f157ae5f745ebfdaa#better-seo-indexing)
+ [Integrating Trello with Teem](https://gist.github.com/krshubham/f8a6024d37c8e50f157ae5f745ebfdaa#trello-with-teem)

**You can find my proposal [here](https://docs.google.com/document/d/1HaltEkAsYoT62oG0lvLRUTTv2iDf1o-sDqRESMbpFgc/edit?usp=sharing)**

*Read on to know more about how I did these*

## Contextual Link Previews
We all are aware of the [contextual link previews](https://meetedgar.com/blog/facebooks-new-link-previews-need-know-2017/) that Facebook provides us when we paste some link. All of the heavy lifting is done behind the scenes and we get to see a card that has rich information contained in that website's metadata. Sounds cool, right? Hmm, why not bring this into Teem's pad and let contributors have a better time here at Teem, because in the end, our goal is to have a consistence User Experience accross the Internet!

The entire part seemed to be very interesting and at the same time allowed me to explore a good part of the codebase. I basically implemented a separate node server which did all the talking between the third party webpage link and Teem.

**The full source code of the teem-link-preview server can be seen [here](https://github.com/krshubham/teem-link-preview)**

#### Pull Request:
+ [**Link Popovers Added**](https://github.com/Grasia/teem/pull/380)

## Better SEO indexing
Another major goal of my proposal was to improve the indexing of Teem webpages also at the same time provide rich meta data content to other external link preview bots from Facebook, Twitter, Telegram etc.
This was one part of the summer which took quite a lot of time which I didn't think that it would take. It was not very straightforward, given how Teem application works, to improve fetching meta data content for crawlers. We know how javascript based web pages cannot render any dynamic content until they are allowed to execute JavaScript. This is the case that happens when a crawler hits a web page. It doesn't execute javascript and well not to our astonishment 😝, the crawler gets greeted by `{{hello}}`. An illustration of the given problem is below:

![Curly braces in gnusocial](https://cloud.githubusercontent.com/assets/7475584/20716845/e8d629c0-b653-11e6-9834-dc778bee88e4.png "When a browser is unable to run javascript")

Those unescaped double curly braces, render the data contained in the variable named hello and in order to get that value we need javascript to be executed. Thus the solution needed to be something like the page should be generated on-the-fly by a server and be given to the crawler. I followed a somewhat similar approach in order to achieve this. But we went through lots of discussions on this. Somedays, we had our(me and Antonio) calls for 1 hour in order to discuss the problems and their solution. Again, without him giving in the thoughts it would be very tough to achieve what we had done together.

### How it looks on whatsapp now:
![Working fine now]()

#### Submitted work
The whole part of the work done in the server that I implemented for my first task and all the contributions were done in [this](https://github.com/krshubham/teem-link-preview) repository.

**Also in order to have a better look on what I did, head over to [this](https://github.com/krshubham/Teem-GSoC/blob/master/Teem_SEO_handling.md) place**

## Trello with Teem
This was again one of the most interesting and challenging part of my project. Due to unavailability of certain features in SwellRT, we cannot do it 100 percent but I'd be very glad in order to make you understand what was the situation that we were in.

Consider our Teem client, a Trello Server and our SwellRT server as the key actors in this small play. We are talking with the Teem Client. Okay, so one fine day I think, why not ask Teem to let me integrate Trello board with itself. The Teem client asked me for my Trello account details and created a new Trello Board in Trello with the name same as the current name of the Teem. Now I asked Teem Client to create a new need and at the same time update it in Trello also. I was happy that it did this for me too. Along with this it did this for other contributors also at the same time.

Now one fine day I was working on Trello and updated a need there. I opened Teem and checked that there was no new need added. I, then ask my Trello Client about the issue and it contacts SwellRT server to get the following answer:
> Hey I was not able to update the data in your needs because I did not get a request from Trello Server about the new need.

After reading this answer, I came to know that there is some gap between how Teem and Trello API communicate and how Teem and SwellRT communicate, thus this is the major difference which stopped me from completing 100 percent of this part! 

For more info on the technical side of this story follow these links:

+ [Teem-Trello-part-1](https://github.com/krshubham/Teem-GSoC/blob/master/teem_with_trello_1.md)
+ [Teem-Trello-part-2](https://github.com/krshubham/Teem-GSoC/blob/master/teem_with_trello_2.md)

#### Pull Request:
* [**Trello in Teem**](https://github.com/Grasia/teem/pull/381)


#### Issue(s) Fixed
* [**Bug Fix: Issue#4: The gulp process should not exit now**](https://github.com/Grasia/teem/pull/373)
* [**Fixing issue with range object**](https://github.com/Grasia/teem/pull/375)

## Next steps:
* Since I was not able to completely work on integrating Teem with Trello, I'd like to be in touch with further enhancements that SwellRT makes towards making its API available in non browser environments.
* Working on to fix some small issues in Teem. I would really like to reduce the number of issues and the issues that are easy to fix.

## Concluding thoughts
It was really fun working this summer on such an interesting and thrilling project. Thanks to my mentor, Antonio, Berkman Klein Center, Harvard University and Google Summer of Code 2017 for giving me the opportunity to participate this summer and spend my summer doing some meaningful work!
