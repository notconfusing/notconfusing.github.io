Title: What Part of "School" Don't You Understand?
Date: 2014-07-04 04:42
Author: max
Category: blog
Slug: what-part-of-school-dont-you-understand
Status: published

I received an apologetic email from [HackerSchool](http://hackerschool.com/) an hour ago, that was sorry to tell me they couldn't admit me this fall - quizzically I was not gutted. HackerSchool is part of the wave of "Hacker Education," where you exchange something with a company for programming education. HackerSchool differentiates in that you don't pay them upfront, or necessarily at all - they just want a cut of a potential recruiting bonus when they pawn you to another company. They also have good perspectives on [lightweight social rules](https://www.hackerschool.com/manual#sub-sec-social-rules) and gender equality which piqued me.  Still, let us not mince, this is private education. A more dedicated Hacker might call it a co-option of DIY, gift-economy culture.

Although this might seem a bitter and fruitless retaliation in response to a rejection letter, that is only the first lily-pad. In fact, there is something more that made HackerSchool particularly attractive to me, which only became apparent in retrospect. As I wrote in my application (which is copied in its entirety below), and [previously about dogs](http://notconfusing.com/lessons-from-dogsitting-the-necessary-collar/ "Lessons from Dogsitting: The Necessary Collar"), a central conundrum for me is not knowing how to work for myself. I can work to impress authorities, appear clever for narcissistic purposes, or for fear of failure - but not because I want to.

HackerSchool's "everyone determines their own lesson plan" philosophy could be a vital stepping stone to a dreamed-of autodidacticism. On the face of it, going to HackerSchool even looks like genuine autodidacticism. But closer inspection would reveal that you have an authority (the HackerSchool institution) that instructs you to teach yourself. The outer loop, the most meta-level, is still a deference to a force that isn't your own. It's virtualizing self-ownership, which is really just ["bluepilling"](http://invisiblethingslab.com/resources/bh08/part3.pdf) yourself.

[![It's virtualizing self-ownership, which is really just ]({static}/images/uploads/2014/07/pill.jpg){.size-medium .wp-image-3508 style="width:300px !important"}]({static}/images/uploads/2014/07/pill.jpg) It's virtualizing self-ownership, which is really just "bluepilling" yourself.

 

This conflict arose during my 14 minute interview with  the organizers, in the question of "how would I learn," my favoured topics? "I suppose, I would use textbook as in College," I replied without confidence, and later amended to "but typically it's been project-needs plus stackoverflow."  In both cases I now see I pointed to historic examples where the main motivator was either a professor or boss. Unsurprisingly this was a lacking answer to both myself, and an interviewer not looking to be my professor or boss.

Looking for positive cases of escaping this servitude, there is obviously one classical logic. Accomplishment-desire drives non-authority-pleasing mechanisms of work. But what if we allow that natural curiosity is not the only way to exit the teach-yourself-to-teach-yourself paradox. What could be alternatives? We could use as a starting point the [goal vs. process](https://duckduckgo.com/?q=goal+versus+process&t=canonical) attitude dichotomy. In this framework the ravenous prodigy sits neatly on the "goal" side. And on the other side?

There isn't a prominent model to represent the unspurred, successful process-worshipper. The best exmaples I can offer are probably something like Aaron Schwartz, [Grigori Perelman](https://www.wikidata.org/wiki/Q117346#sitelinks-wikipedia), or a stereotypical monk. Having such a dearth of role models is probably because process-oriented people aren't highly lauded in our prize-counting society, and are thus non-notable. This is a dead-end I feel I've been running into frequently.

The conclusive feeling here is not directed, but is still a redoubling of effort. It's a large, and still partially free internet out there. There's Open Access research to read and write, and Open Source code to execute and develop. Even without the promise of coming to an epiphany of how not to get depressed about the fact that I do it alone in my bedroom, that unlit corridor still calls to me as the one with light at the end.

------------------------------------------------------------------------

Should it help anyone fulfil their dreams, and for the sake of radical transparency, this was my [HackerSchool Application](https://www.hackerschool.com/apply).

### **HackerSchool Application**

### **Links**

**Please include any that you have: GitHub, LinkedIn, personal web site, etc.**

 

<http://github.com/notconfusing/>

<https://www.linkedin.com/pub/maximilian-klein/4/b1b/63> Any tips for updating?

<http://notconfusing.com> (trying to fix width issue on category subpages may need to switch thee)

### **Code CracklePop**

**Write a program that prints out the numbers 1 to 100 (inclusive). If the number is divisible by 3, print** ***Crackle*** **instead of the number. If it's divisible by 5, print** ***Pop*. If it's divisible by both 3 and 5, print** ***CracklePop*. You can use any language.**

 

    rice = [3,5]

    crispies = ['Crackle','Pop']

    rice_crispies = dict(zip(rice, crispies))

    for i in range(101):

        print(i)

        for flake in rice:

            if i % flake == 0:

                print(rice_crispies[flake], sep='', end='')

                print('', end='\n')

 

### **Please link to a program you've written from scratch.**

**You can use something like**[**GitHub's gist**](https://gist.github.com/) **to host your code. It doesn't need to be long, but it should be something you've written yourself, and not using a framework (e.g., Rails). If you don't have anything to submit, code something small, like a game of tic-tac-toe.**

 

This tutorial translates an Economic algorithm into Python. In short, it does some matrix-calculations, statistical analysis, and some plotting. Its most advanced language-feature is a python “generator.”

<http://nbviewer.ipython.org/github/notconfusing/wiki_econ_capability/blob/master/Method%20of%20Reflections%20Explained%20and%20Exampled.ipynb>

### **What is the most fascinating thing you've learned in the past month?**

**This doesn't have to be about programming.**

 

We all know a averaged crowd of fair-goers can guess the weight of a heifer more accurately than any of the individual simpletons among them. Science shows the principle extends to marbles and encyclopedias as well. But what I picked up this month at the Network Science Conference ‘14, was that it can be applied to stock trading too. Diversification strategies work - but they can also be diversified. A team of researchers explained a technique that they simulated. If you followed x traders, mimicking exactly the trades they perform, but with 1/x of your money, then for sufficiently high x, the return is higher than any of the individuals.

 

The network science bit comes in because you don’t want anyone you follow to be following each other. For the highest return on investment, those who you follow should have “no common ancestors,” in network parlance.

 

More so than stock trading, the “wisdom of the crowds” theory appeals to me. Trying to make clever stock decisions is a huge industry, and this intuitive simple mechanism can compete with more complex ones. What’s fascinating here to me is how theories can unexpectedly translate between domains.

### **What do you want to be doing in two years?**

 

Two years from now I would like be swimming through the gooey centre of a large research project at a think tank or in research and development. Stemming from my previous employment at OCLC Research (a library think tank), I enjoy the freedom of blue-sky thinking. Therefore the employers that have a large enough budget for pure research (Microsoft Research is a good example of this) are the competitive waters that I want to compete in. Having such lofty dreams are never regrettable in my experience because there are always failsafes. In this case one can always sell oneself as a Data Analyst for business intelligence.

 

To enjoy any future work however it would be crucial for me to be in a team of stellar collaborators. My personal adage (which I stole from a guy that works in a copy shop) is “life is the water cool, the water cooler is life.” Being around people ignites my mind (even at the copy shop), and I want to continue fuelling that fire. I will continue to invite uncomfortable differences in perspective. Therefore in two years I want to be in a team that values learning over goals. Goals inevitably follow learning - but not vice-versa.

### **Why do you want to do Hacker School?**

I see Hacker School as the centre part of a venn diagram of my desires which are (1) learning self-directedly (2) being part of a supporting group, and (3) boosting employment opportunity after.

 

Last year when I went to my boss and asked her to crack the whip on me harder, my own actions perplexed me. I quit my job to attack the problem of relying on authority to motivate my work. But next came the paradox: how can one self-direct one’s self to autodidactically become self-directed? Recursion without a base case.

 

From a pragmatic perspective I still go to my local hackerspace because I enjoy what could be termed as “co-learning.” The social environment drives me. Being conscious of your impression on others, can psychologically push you to work. It’s not self-actualizing alone in your bedroom, but it’s effective.

 

Hacker school seems like a realpolitik compromise between bootstrapping self-ownership, and well-proved social dynamics. Given that Hacker School can also help with the personally-dreaded task of a job-search after, I see a trifecta being won.

 

### **What would you like to work on at Hacker School?**

**E.g., things you want to learn or understand better, projects you want to build or contribute to, etc.**

 

While there are a few pet-projects that jump to mind, none are as important as the process of the work I might do. Rather than pronounce any work in detail, I would describe my desires declaratively. There are two main criteria. Firstly, like a carrot just beyond horse-mouth's reach, I want to find a project that is harder than I expect, simply to level-up. Secondly, is to overcome the folly of the lone-inventor myth. To horizontally work with a partner is as important as being the bringer of the techno-revolution. So the thing I would like to work on is a new idea I would receive while I’m at Hacker School.

 

That being said, in absence of any external input, a few of the topics I want to understand better are machine learning, genetic algorithms, and pattern recognition. These corners of computer science are somehow just cool. Pursuing them, since they are substantially complex seems commensurate with Hacker School motto of “get dramatically better.”

 

Also I want to be able to make my phone turn off silent mode by sending it a secret text for those hidden-under-couch situations.

**Programming background**
--------------------------

**This information** ***will not*** **disqualify your application. We use it to better get to know our applicants and where they currently are. If you're worried that you won't fit into Hacker School, you can read about**[**some of our alumni**](https://www.hackerschool.com/alumni_profiles)**.**

### **Describe your programming background in a few sentences.**

2006\. Failed Java in Community College.

2009\. Discover I enjoyed programming Turing Machines on paper in "Computability Theory" in my Pure Math major.

2010\. Enroll in – and revel in – the purity of the Berkeley/MIT Scheme tradition.

2011\. Fail Java again. Tech career funeral and wake.

2012\. Phoenixed with Python + Stackoverflow, to write Wikipedia bots.

2013\. Welcome to the FOSS movement. Linux and git start unpacking in my brain.

2014\. Hacker School

 

### **Have you worked professionally as a programmer?**

**If so, please describe your experience.**

 

Working in programming and working hard at reinventing the idea of a “professional” programmer have been the last three years of my life. When I was “Wikipedian-in-Residence” I turned my job into programming by convincing management of my proposed bot-writing projects. In my own business I’ve won contracts to deliver reports that were the result of custom programs. So although I’ve never worked as a typical professional programmer, I like my life to be about delivering code for pay.

 

### **Do you have a Computer Science degree or are you seeking one?**

 

I have a Bachelor’s degree in Mathematics from University of California Berkeley, and have applied and furthered my Computer Science knowledge outside of academia. In the far future I have considered enrolling in a  Master’s or PhD program. My draw towards a heavily mathematical emphasis looms. From my work with Wikipedia, a more human and social element has nestled in my head. Therefore it’s possible that my interests would converge in Computer Science degree.
