Title: Design for Doulas
Date: 2016-02-22 02:09
Author: max
Category: research
Slug: design-for-doulas
Status: published

I have typically avoided the realm of UI design, as I view as fraught with of cults of personalities and nonstop bikeshedding, but this semester I decided to try my hand and find seperate the theory from the style posing as theory. The course I am taking is centered around a large project to design an application that helps a population of people with a need they have. This coincides nicely with a dream I have harbored to make technology for [doulas](https://en.wikipedia.org/wiki/Doula)- providers of nonmedical, practical and emotional support for pregnancy.  My partner is a doula and leader in a doula organization, so I have been somewhat privy to the way they use tech to run their program. What should come as a shock to no one, is that there do not exist any applications that are tailored for their kind of work.

If there is one main thesis coming out of UI Design theory today, its that it ought to be [user-centered](https://en.wikipedia.org/wiki/User-centered_design). That is, the design should suit the needs and expectations of the users, not the programmers making it. In this vein, the only way to start our project (I am working in a group of 4 other students), was to get some input from birth workers.

With the help of my partner, we sent out a request to some list-serves about what doulas think are technical debts opportunities at the moment. In fact we received a very quick response:

> <div>
>
> I've been thinking about an app for black pregnant women; that would connect them with doulas and resources. I don't know if that's what you had in mind though since you mention care providers rather than the women themselves. There is a huge gap in info for black women who are interested in alternative birth.
>
> </div>

<div>

</div>

It was fantastic to get such a clear signal for a need for such an important and undeserved population. It really excited me having a direct request to make an app for black pregnant women, and I followed up with the requester of the idea. But after some consideration I felt that it might be irresponsible to take on the assignment. The reasoning was that, although I am very dedicated to the idea, because I am doing it for class, there is a distinct possibility of the end product not being very polished in the short-term. In addition, the design process requires time and input from the users for prototyping etc. If we didn't end up making an app that was very useful for black pregnant women we would in essence be using black pregnant women to get "A" in a class. That seemed like a very perverse backfiring of good intentions and privileged people misappropriating the efforts of less privileged people.

We put out more calls, and eventually made contact with another doula organization that was willing to work with us, with explicit disclosure of all the risk and time involved in taking on designing a tech project. In fact a partner of one of the doulas is a computer science student like ourselves. This is the basis for what makes working with doulas organizations potentially less dangerous than black pregnant women. I believe that work for social good with people that aren't like myself should come in the form of strong partnership and allyship. In this case my closeness to my girlfriend's\* connection to doula work allows me to be a closer partner in making tech for doulas than black pregnant women, of which I know none at the moment.

\* (Using the term "girlfriend" to distinguish between "partner" in the make-a-family-together sense and "partner" in the make-technology-together sense)

We have commenced work with a doula organization which I will not name out of privacy concerns. As per UI design protocols our first step was to conduct [contextual inquiries](https://en.wikipedia.org/wiki/Contextual_inquiry) with our potential user base. A contextual inquiry is  an inspection of the practices of the user, what is important to them and what are pain points they experience in their work. The advised approach is one where the designers are "apprentice" and the users are the "masters". This mindset tries to stop designers preconceiving of what the user will want.

One of our inquiries was with the leaders of a doula organization which focuses on support for birth, and the other which focuses on support for abortion. In fact finding the overlap and underlap in the needs of these two user bases was fascinating, and have many design implications. In terms of **similarities**, we found needs in anonymity in client-doula matching.

### Anonymity

The role of the organizations are to connect together clients and doulas. With birth, and particularly abortion, keeping the everyone's identities anonymous until a match is made is crucial. At the moment, a leader of the doula organization will collect requests from clients, anonymize them, and then advertise the requests to doulas. Doulas that would like to work with the client are then relayed back to through the organizer. Once the client accepts the match, only then are identities and contact information exchanged. Certainly we can automate part of this workflow to assist a leader in matching: automatically stripping out names and contacting doulas, autoshuttling these responses back.

An open question that takes this a step further is if the matching can be done *anonymously without a centralized* connector of the two sides.

### Platform

Of course the designs above are similar to other online systems that assume the use of email. For people that are looking for a doula in these contexts - not to mention the expense of healthcare in the United States - email or web access is not guaranteed. In fact in the contextual inquiries we found that the most common form of communication was the plain old telephone. This means that interaction through text-messaging, or touch-tone phone systems would be required for full automation on the client side. Luckily on the doula-facing side emailing is much more standard, which makes solving the problem partially through more standard means more tractable.

Still the **differences** between birth work and abortion work surfaces even more hard to see design implications.

### Choice vs. Speed

One junction in matching is sending the client back their potential doula matches. In birth work, we found that this organization likes to emphasize *choice *for the client as way to empower the client. That means that the organizer will wait an amount of time for many doulas to respond to client request so that they can relay several choices back. On the other hand we heard from abortion workers that *speed* is most important in matching, due to abortion options being more time-sensitive. In this case the first doula responding is returned to the client. Any system trying to accommodate these needs will have to use varying mechanisms.

### **Follow** up

Famously, facebook has been criticized for their "memory" sharing because it can bring up aggravating memories of a break-up or other hard times. As we heard, in the case of abortion work, following up with a client can also painfully and accidentally remind a client of their abortion. However in birth work scheduled follow-ups with clients are standard practice. Therefore a system should be extremely sensitive about when, and to whom, the system will send messages. For instance, maybe even in the case of say a password expiration it would be better not to e-mail/text the client from the system, but to perform an alternative internal action.

 

These are some of the observations that we have have made so far. We still have prototyping and building phases to complete. I believe the design of doula organization tech is valuable and unexplored territory in UI design, and valuable for feminist HCI (human computer interaction).
