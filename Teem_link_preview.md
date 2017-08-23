## Teem-link-preview

This is the part that I had done for the first evaluation portion of the Google Summer of Code.

**Goal**: To add the functionality for contextual link preview in the teem pad

###Implementation steps

+ Firstly we have a docker container that houses the server which does all the processing to bring the contextual link previews. The main file that handles all these things is: [here](https://github.com/krshubham/teem-link-preview/blob/master/src/routes/fetch.js)

+ The basic way in which this server works is shown in the below diagram:

![Working of link previews](http://krshubham.github.io/images/Teem-link-preview-working.png "working of teem link preview") 

+ After seeing the image I hope that everything is clear. Here is the PR for the work that I have done: [PR#380] (https://github.com/Grasia/teem/pull/380)


+ Blog post: [Gsoc-Part-1](http://krshubham.github.io/blog/2017/06/29/GSoC-part-1/)


Here are some screenshots of the work done:

![Loading the preview](https://krshubham.github.io/images/gsoc-part-1_2.png "loading the preview")

![The preview] (https://krshubham.github.io/images/gsoc-part-1_1.png "preview is ready")


### Installation 

You can see in this [commit](https://github.com/Grasia/teem/pull/380/commits/997258f2b85d98bdc1207792d0f0296eb0189308#diff-12f0222a60ecdccbafce925ddac9500dR18) that I have added the docker repo in the config file for docker-compose. So, it should pull itself automatically.


### Issues and further development

As mentioned in the pull request, we still have some issues which are:

+ Adding proper styling to the popover
+ Some issues in editing the SwellRT annotation while simultaneously hovering over the popover.

 
 

