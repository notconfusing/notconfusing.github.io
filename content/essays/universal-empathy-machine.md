Title: The Universal Empathy Machine: Nonviolent Communication Explained with Mathematics and Computer Science
Date: 2015-07-28 06:00
Author: max
Category: essays
Slug: universal-empathy-machine
Status: published

0. The Universal Empathy Machine
--------------------------------

Empathy is not sympathy. What's the difference? Think of the [Universal Turing Machine](https://en.wikipedia.org/wiki/Universal_Turing_machine). It is a machine that accepts a program and data, and runs that program on that data. In this way it can simulate all programs on all data. Let us think of a human as a program and human experience as data. **Sympathy then, is running your program on someone else's data. Empathy is running their program on their data.** As you can see the results of the sympathy and empathy computations are not guaranteed to be identical. In a nutshell Nonviolent Communication is about becoming the Universal Empathy Machine, to be able to emulate the architecture of an arbitrary person given an arbitrary experience.

 

Introduction
============

[![Cover of Nonviolent Communication, replete with sunflower]({static}/images/uploads/2015/04/nvc_cover.png){.size-full .wp-image-3755 style="width:173px !important"}]({static}/images/uploads/2015/04/nvc_cover.png) Cover of Nonviolent Communication, replete with sunflower

*Nonviolent Communication (*abbrv'd *NVC)*, is a theory by [Marshall Rosenberg](https://en.wikipedia.org/wiki/Marshall_Rosenberg "Marshall Rosenberg") and the title of a book which has an unfortunate cover. Dressed up in a sunflower, you would associate it with self-help pseudoscience and may not allow it to surprise you. I only popped it open because *a)* it could be pirated on The Pirate Bay, and *b)* it was the reciprocating recommendation to me after I had been proselytizing my then-favourite-read to a friend, and so I felt obliged. As you can see neither of those reasons should really have you running to the library.

Its insight-olives are sparse in its ciabatta. But however rare they are, those morsel were escape plans for decade-long arguments. I felt so resourceful having a theory of dealing with conflict where I never had one before. The only problem was I couldn't chat to my friends about it, let alone recommend it. (Update: which now turns out to be [a common phenomenon](http://2013.dareconf.com/videos/sauer)). It's not intended for anyone that would use the terms *logical*, *or reasonable* to describe themselves*.* They'd be seeking different analogies, examples, and want it to be quite a bit shorter.

Well this is that version, your very short introduction to Nonviolent Communication, abridged and explained through mathematics and computer science analogies. I'll translate it into the realm of motivations, axioms, communication protocols, and finally foundational flaws.

1. The Intention of Nonviolent Communication is Connection
----------------------------------------------------------

Any good sceptic should immediately be asking the purpose-question. What we are interested in is the family of problems characterized by the set of disharmonies, disagreements, and arguments.

Now it must be noted that nonviolent communication admits to there being intractable arguments. Not every argument is solvable, and **like the halting problem, there is no way of deciding whether an argument will run forever** without just trying to solve it.

The main approach we use to arguments is *finding* *connections.* A connection is relation \$latex aRb\$ between persons \$latex a\$ and \$latex b\$, not necessarily distinct, such that \$latex a\$ and \$latex b\$ are ready to resolve the disagreement. (What is it when one person is not ready to resolve? We address that later).

Argument resolution often never starts because it does not aim to find connection. In some cases we are talking past each other, we need to connect onto what the main topics are. In other cases we are discussing the same topic, but cannot connect onto a mutually agreeable answer, here NVC says to connect on observations and feelings and needs.

> Protip: Notice connection is not always with "others", because often we want to change abusive self-dialogue.

2. Axioms of Nonviolent communication
-------------------------------------

There are three strong axioms; sorry Wittgenstein fans.

### 2.1 Feelings Are Connected to Needs

We suppose a *Connection* map, which maps feelings to needs.

\$latex C \\colon F \\mapsto N\$

Where \$latex F\$ is the set of all feelings, and \$latex N\$ is the set of all needs. Note that \$latex C\$ is not necessarily injective but is surjective. The intuition here is that whatever feelings are observed, can be map to a need - probably unmet. This need usually becomes our focus.

### 2.2 All Needs Matter

The set of needs and important needs are exactly equal.

\$latex \\forall n \\colon n \\in \\{ \\text{needs} \\} \\iff n \\in \\{ \\text{imporant needs} \\}\$

Taking as an axiom that all needs are important needs allows participants to declare needs without fear. The Universal Empathy Machine is a system of how to accept needs as important which do not appear important, *to you*.

### 2.3 There Is Always a Choice

The empty set is not contained in the set of all choices.

\$latex S := \\{ s \\in \\mathcal{P}(choices) \\wedge s \\neq \\emptyset \\}\$

Let's consider this our "Axiom of Choice" - we always have one. NVC asks us to accept a strong theory of free will. We have a nonempty, and possibly infinite set of reactions for all interpersonal interaction.

3. Communication Protocols
--------------------------

In trying to connect we will have to in some way communicate with each other, let's call this *messaging*. NVC says that it's important to do this in a specific way. The messages that we pass between objects, probably humans, not necessarily distinct, are a 4-tuple containing:

\$latex messaging tuple := (observations, feelings, needs, requests)\$

This quadruple through the unveiling of each element, produces a flow from empiricism, to emotion, humanism, and finally to action.

Not every message needs to contain all four parts, for brevity often they can be omitted. When starting though it can be useful to be exhaustive for practice.

### 3.1 Observations

    "Observing without Evaluation" 
    ~ NVC Chapter Title 3

In the canonical specification of Nonviolent Communication, this chapter is literally titled "Observing without Evaluation". Little do they know just how apt that is. In this messaging block we are transmitting our observations rather than our opinions. The assumption NVC operates with is that when viewing the world, we sense our observable universe and then evaluate it to return opinions. But it is not clear that those opinions are useful yet, so let's not naturally default to *eager* *evaluation*. (Well you may not, depending on how much of a functional purist you are.) Taking a cue from the *lazy evaluation* model, we don't have to return opinions until they are necessary. In fact, evaluation is not necessary until we send *feelings*.

If you are not a fan of fixed evaluation strategies, another way to think about the observation section is it's where we make our *imports*. Here we are providing the populated namespaces, libraries, *Connection* API and constants that we will reference in the rest in the rest of our communication. The context. Since sensory perception varies from human to human, we cannot rely on the exterior universe to be observed equally, thus we pass along our context. The point is that we do not want any of our further statements to be received ambiguously, so our definitions must be precise. We make only natural-philosophy-style remarks that equate to be exactly true. "You're always late," has truth value in the open interval \$latex (0,1)\$ depending on which human is observing. "We agreed to meet at 7:30, and I saw you arrive on Monday at 7:45, and on Tuesday at 8:05" has a truth value of just \$latex 1\$. Now the rest of our program, or proof - whichever side of the isomorphism you prefer - can refer to lateness with no misgivings.

#### Exercises: Observation or Opinion?

1\. "Your email signature is 41 lines long, rendering for me as over 4 screenfuls, where as your last 5 messages to the list were each less than 41 lines long."  
2. "Dante often does not wash his dishes in the hackerspace."  
3. "Allesandra told me that I was not good at identifying contrapositives."  
4. "Our group facilitator controls the meetings."

#### Answers

1\. This is an observation, which is entirely verifiable.  
2. This is an opinion because "often" is not defined.  
3. This is an observation if Allesandra literally said so, but not if Allesandra was only referring to a specific time the speaker [did not identify a contrapositive](https://en.wikipedia.org/wiki/Wason_selection_task), in that case the speaker would be making an evaluation.  
4. This is an opinion because "controls" is open to interpretation.

> Protip: when you are having difficulty finding observations to base what you want to say, and your communication is a reply it is OK, and even encouraged to literally repeat what your partners have said. \$echo what-they-said. More about this in **4. Receiving** section.

### 3.2 Feelings

    There is the counter-intuitive Rosenberg law: "Expressing our vulnerabilities can help resolve conflict."

After having carefully preserved the pre-evaluation *observation*, it is finally time to also give the results of our evaluations - *feelings*. To explain what feelings are we explore a classic gotcha - *psuedofeelings.* Pseudofeelings unfortunately do pass duck-typing tests. They key difference, is that, with respect to the feeler, feelings are internal, and psuedofeelings are external.

Some examples of pseudofeelings are "I feel unimportant", "I feel misunderstood", or "I feel ignored". Re-expressed as feelings these would be, respectively: "I feel discouraged because I observed I was not part of \[important decision\]". "I feel anxious because you doing \[action\] doesn't reflect that you understood me.", "I feel hurt, because I perceive I am being ignored.". These re-expressions take an external feeling, and talks about what external event made you feel internally. This is important, because a statement about yourself can never be blaming, and allows others to see your perspective on your observations.

#### Exercises: Feeling or Pseudofeeling?

1\. "I feel scared when you talk about about forking".  
2. "When you don't cite me, I feel neglected."  
3. "I'm happy that you found time to come to Wikimania."  
4. "I feel disappointed by the fact that you did not publish your dataset, because I had to recreate it."

#### Answers

1\. Feeling. Scared describe's the internal state of the feeler.  
2. Pseudo-feeling. Neglect is a thought about the exterior world. Feeler is probably *depressed* about not having their work recognized.  
3. Feeling. The user happy, and said so.  
4. Pseudo-feeling. Despite very clear reasoning, disappointment is not a feeling, but a pseudofeeling. User is probably feeling aggrevated because of needless extra work.

### 3.3 Needs

    "God gave us the universal needs, man created the rest" 
    ~Einstein

We have described the outside world, and stated how we feel about it, but we'll require one more step to expose our "*Connection* API". **Needs are those sufficient and necesarry condition for you life.** According to NVC all humans come preloaded with immutable natural feelings which are factory defaults. Because needs are very low-level, primitive objects, it s likely that the communicators will have some of these in common. And with common needs, connection can be found.

Needs are typically very basic, like: autonomy, celebration, creativity, appreciation, love, respect, play, peace, food, rest, sex. Communicating these needs may seem weak, irrational, and impossible to admit out loud, but the whole point is to open up. **This point is opensourcing ourselves to the very lowest machine-level.** There are two ways in which this Richard Stallman doctrine aids us with emotion. First, the open code of ourselves is a signal for our partners to work with us, and the mystery of how we work disappears. Secondly, when we disclose our code, all bugs are shallow. It is scary that others will be delving into our innermost code, but like Heartbleed, it is the only route to long term security. Remember**,** in order to further our opening have the **Axiom 2.2**, the safety mechanism that all needs are important.



#### Exercises: When Are Needs Being Expressed?

1.  “I feel angry when you talk about transhumanists that way, because I am wanting respect for my own destiny and I hear your words as an insult.”
2.  “I’m discouraged because I would have liked to have progressed further in my work by now.”
3.  “I feel disappointed because you assigned yourself to those bugs, but didn't squash them.”
4.  “I’m sad that you won’t be meeting me at the vegan restaurant for dinner because I was hoping we could chat about anarchism together.”

#### Answers

1.  Wanting respect for way of life is a basic need, whatever it may be.
2.  This is close enough to a need. It is implied that the need to is for the speaker to be feel fulfilment from progressing through work. This is actually an exercise verbatim out of the original NVC book.
3.  No need is being expressed here. Perhaps the speaker needs the mental comfort of having no outstanding issues, or needs the security of that comes with trustworthy friends - we don't know and it isn't clear.
4.  Human contact is a need. Maybe they also need a tempeh gyro.

### 3.4 Requests

    Callbackhell.com's author Max Ogden analogizes callbacks to the numbers given you at restaurants that tell waitrons what to do with your food after it has been cooked. In our case, it is more like the waitron telling you that their job has many harsh realities, which makes them feel very oppressed, crushing their need for economic freedom, and finally telling you to help them smash the capitalist wage-labour sociopolitical complex.

At last we can try to alter the world with requests. Requests are callbacks we send to our communicating partner. They indicate what and when we'd like your partner to do. Like asynchronous javascript, there are a lot of security issues. Co-communicators won't want to run to malware. That's why the best request-callbacks are verified non-malicious by being the conclusion of a observation-feeling-needs-request syllogism.

> Protip: By **Axiom 2.3** we always have a choice, and so it is impossible to be in a situation where only the other party can break a stalemate.

Issuing precise requests clarifies what we want from our partner. If it feels difficult to articulate what we want from others, that's typically because it is not an action. NVC says that more specific actions make better requests, otherwise we're issuing request that the receiver can't know if they've done it. If we shout at our colleague that a project is behind schedule, and we know they can't speed it up - we're not asking them to speed it up, but merely to acknowledge our anger. In this case the call back request might be "give receipt of my frustration". Colloquially this would be known as venting. It is nice to have no ambiguity about when the roles are just to listen, or to actually address a behavioural pattern.

#### Exercises: Request or No Request:

1.  “I want you to grok me.”
2.  “I'd like for you to indicate one moment in my presentation that you appreciated.”
3.  “I would like you to walk more slowly in the airport and tell me where you're going before you walk off.”
4.  “I want you to be proud of your organizing work.”

#### Answers

1.  Not a request, because grok is not specific action. It could however be illustrated by asking for the receiver to paraphrase speaker. (See how to do this well in ***4. Receiving***)
2.  This request is asking for a something concrete, empathetic reception. These kinds of requests are made to seem ridiculous in the modern era, but that is just the long term cultural effect of "[guess culture](http://www.thewire.com/national/2010/05/askers-vs-guessers/19730/)".
3.  A little bit exasperated, but quite clear actioning in the request. This isn't not not one of my pet peeves.
4.  How is the speaker going to know when the receiver is being proud? "I want you to tell my friends about your organizing work," is more direct if that's what they're looking for.

4. Receiving
------------

NVC's messaging protocol is two-way, and now that we've covered *"expressing honestly"* there's still *"receiving empathetically"*. Receiving empathetically can be understood as the process of parsing unstructured conversation text into the formal grammar of NVC. The conversation text is what the other person is telling you and our target grammar is the observation-feelings-needs-request 4-tuple. We are not guaranteed to get all of the components, and not in any specific order. We've just got a really difficult parsing problem on our hands.

The reason that people are offended when they are asked, "Did you hear me? What did I say?" is because it s actually difficult to paraphrase what may already be a hard message to hear. We will attempt to do better, to translate their communication into an NVC object. Once we can be sure we have their experience (data), and how they are dealing with that experience (program), we can become the Univeral Empathy Machine (**section 0**), and be fully empathetic. When done right the empathetic affect will come alive. Firstly, and very clearly their need to be just-listened-to will be fulfilled. More subtly, our partners can fine-tune their thinking *by seeing how closely our Empathy Machine mirrors their Identity function.*  That is, how well our reflection matches their intended expression. This lets them know if we are missing any of their points, or they haven't stressed what they would like to.

> Protip: Even if someone starts trying to brute force attack us with volume and vitriol, we can still receive empathetically. Intimidating messages are also people asking us to meet their needs. Try for instance, "It seems like you're really angry about my deleting the private key; because you need more security about what's happening in your life." Likewise, if we are engaged with someone not ready to resolve, see if an application of empathy towards them helps.

Counter-intuitively this paraphrasing saves time, even though it takes time. A typical pitfall in a time-saving mentality of receiving is the bad habit of trying to short circuit the conversation by offering unsolicited advice to people. Offering unsolicited advice would be as if a parser (a) took input, (b) maybe did or didn't parse the input, (c) did not verify the meaning of the maybe-parsed result, and then (d) returned advice based on exogenous heuristics. Returning that computation to the speaker would understandably be nonplussing if not absolutely frustrating as it is devoid of any indication that it related to what they said. Giving advice is only useful *iff* advice is what the speaker is asking for. By assuming they want a “fix-it” response, we are only engaging in the folly of *[mansplaining](https://en.wikipedia.org/wiki/Mansplaining).  
*

Receiving empathetically is to parse our partners messages and run it through our Universal Empathy Machine.

#### Exercises: Empathetic Reception (Y/N)?

1.  **Person A**: Counting error in Ultimate Street Fighter IV finals? How could I do something so stupid? **Person B**: Nobody's perfect, don't be too hard on yourself.
2.  **Person A**: You're a delusional utopian.  
   **Person B**: Are you feeling frustrated because you would like me to admit that there could be other ways of interpreting the Black Lives Matter movement?
3.  **Person A**: Oh I’m being SO BAD! I NEVER eat cupcakes! **Person B**: Maybe exercising more would help you.
4.  **Person A**: When friends of a friend of a friend join our camp without showing commitment, I feel encroached on. It's like how fraccing companies squeeze me with anti-protest tactics. **Person B**: I know how you feel. I used to feel that way too.
5.  **Person A**: I’m unhappy with the grant's status because you should have made more impact by now. **Person B**: I know you're unhappy, but we've been slowed by bureaucratic process.

#### Answers

1.  B is giving advice to A, which is not an empathetic response. "You sound like you're enraged by your lapse of concentration," is more along the NVC lines.
2.  Empathetic response since B is trying to ascertain from A's perspective why A might be lashing out.
3.  Again B is advising A, even though the tone is lighter. B might want to try and understand what feelings are behind A's [not being neutral about food](http://queerfatfemme.com/2015/06/25/neutral-about-food/).
4.  Not an empathetic response, an sympathetic response. Same data, but whose program is being applied?
5.  Trick empathy. Just saying you understand is not the same as demonstrating you understand. B left A's comment about impact on the floor, which B could have used to empathise with.

5. Criticisms of NVC
--------------------

How many different input methods can we use to write an email? Maybe with a physical keyboard, or virtual one on a phone, [different auto-complete](http://sangaline.com/blog/optimizing_for_swype/) schemes, speech-to-text, and maybe we've even had the pleasure of tapping one out T9 stylee. Even though we may aim to transcribe the same thoughts, based on the technique used, the final text will be different. If the text of our emails are altered so too are the conversations. Now, different formats of email it will benefit specific ways of writing. We might be happy arranging dinner plans tapping on glass, but for conforming to the standards of a formal letter begs for the old clickety clack.

As input methods change a conversation, so does NVC. Since it is very literally a theory of discourse, using NVC will necessarily bring with it *prediscursive* bias. The format of the discussion is not variable that is discussed. But fair enough, any communication strategy would come attached with its own biases. The question then really becomes, *since NVC is prescribed conversation format, which speakers does it benefit*?

NVC's founding theorist, was an American white man born in 1930 as the son of Russian Jews. What does that mean specifically for who NVC benefits in conversation? My reading turned up no mention of how Rosenberg's personal background might affect his theorizing. In my opinion - I am myself a white man with similar citizenry and ancestry - it imports notions of classical logic, a Mazlowic need hiearchy, and western rationality.

To expand, the technique has an orderly system to follow. This system is static and procedural, where it could be more goal-directed. The ontology presupposes the universality of basic needs. This could be interpreted as the hubris of someone currently with privilege assuming that others are like them. And lastly it does not make large mention of how it would fit in a multiplicity of different communication strategies, as a pluralist might.

Conclusion
----------

NVC has a grand concept, which works at times and is undermined by it's flaws at others. It was useful for me because it was the first conflict strategy I'd heard of, and it "made sense" to me. It turned out not to be a persuasion-hack, but it did teach me the concept of empathy. Understanding empathy for the first time was truly a dose of mind expansion. I've kept the format of NVC's exercises at the end of each chapter, because as contrived as it seems, the questions are hard, empathy is not intuitive, and practice is vital. It's really more praxis than theory. In fact, practising empathy has been the inroad to new ideologies for me like: feminism, anti-racism, LGBTQ-allyship, and other social movements for which I am not the effected demographic. I hope you, person who likes mathematical analogies, can glean something studying from it too.
