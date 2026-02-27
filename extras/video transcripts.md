So what you're looking at right now 
 isn't clawbot isn't open claw nano claw 
 or any derivative. It's actually cloud 
 code on my desktop running in telegram. 
 And it's just as good if not better than 
 openclaw out of the box. And I've even 
 managed to make it multimodal. So if I 
 take my phone right here and I take a 
 video of myself momentarily and 
 switching over to my actual desk and 
 showing it my screen, showing it my 
 laptop and I send that over. You'll see 
 it goes right here. It's able to 
 interpret. And you'll see on the left 
 hand side, my cloud code is 
 initializing. It's running on my real 
 desktop with all the skills and 
 everything it needs to process and 
 understand this video. And after 30 to 
 40 seconds, our new Claude Claw comes 
 back with a full interpretation of the 
 video. So, it says, "You're showing off 
 the setup, panning from your face to the 
 Mac Mini with your microphone setup and 
 the monitor along with the MacBook." So 
 we don't only have access to video 
 interpretation but we can create images 
 with nano banana to ask it how cloud 
 code works. We can make it respond to 
 telegrams, WhatsApps, whatever you want, 
 as well as explain to us how it's built. 
 Now I spent weeks trying to make 
 openclaw work for me to the point where 
 I tried to make a derivative that I 
 shared on this channel and even that 
 wouldn't stick. So then I was pushed and 
 led to ask the question, why not just 
 make my own personal assistant using my 
 existing cloud code? In other words, why 
 not just use what you have and be able 
 to interact with it remotely from 
 anywhere you want? So in this video, I'm 
 not only going to walk you through 
 exactly how I did it, but also how it's 
 designed and how you can do it, too. By 
 the end of this video, you're going to 
 have a personal assistant infinitely 
 more tailored and powerful than 
 OpenClaw. Let's dive in. So, I'm first 
 going to walk you through the entire 
 infrastructure and the concept of how 
 and why this works. And then I'll show 
 you this mega prompt that I've put 
 together that should set you on the 
 right path to build it yourself. So, my 
 goal is that by the end of this video, 
 you could take that mega prompt and you 
 could take the transcript of this video 
 and essentially feed that to your own 
 version of Cloud Code and have it self 
 build its own version. The main concept 
 here is we just have a medium. In this 
 case, our medium is Telegram and we have 
 a bridge. This bridge is not some third 
 party we have to worry about. It's 
 actually Anthropics native agent SDK. 
 And this SDK will allow us to bridge and 
 create our own cloud code terminal that 
 we can tap into. And once we have access 
 to it, you essentially have access to 
 the same terminal and the same 
 underlying infrastructure on your 
 computer. So in my case, I have 30 plus 
 global skills, MCP servers, cloud MDs 
 across different projects. I have web 
 search and I was able to create and 
 customize my own version of memory along 
 with using my existing file system all 
 from a few simple commands. So to be 
 clear on where I stand, OpenClaw was the 
 4-minute mile. It was the breaking of 
 limiting beliefs that we didn't have all 
 the technology we needed to build a 
 personal assistant at this magnitude. 
 But the flaw with open claw or formerly 
 claudebot was it was basically patching 
 together different ways to create the 
 existing harness of cloud code that 
 already exists and is already 
 exceptional. So even when I decided to 
 replicate and clone every single version 
 of repository like openclaw, like 
 nanoclaw, like picclaw and recreate it 
 myself, it worked. It was a lot faster. 
 It was mine. But I still had to always 
 do dual entry. So if I had a particular 
 skill that works perfectly on my desktop 
 version of cloud code, I would always 
 have to pipe a version of it to work 
 with this new creation I made. If I 
 wanted to schedule something, I'd have 
 to run it somewhere in the cloud. If I 
 wanted to worry about security and 
 authorization, I would have to audit 
 each and everything I'm doing. So after 
 realizing I had to mass customize and 
 continually maintain all the burden of 
 the brand new version I created of 
 OpenClaw, I realized I basically created 
 a derivative of a derivative of a 
 derivative. So there had to be a simpler 
 way and luckily there is. So in the old 
 way, and when I say old, I say this 
 jokingly because this was literally last 
 week. I would take an existing version 
 of this repo, replicate it, customize 
 it, go back and forth with cloud code 
 until it worked perfectly for me. But in 
 the new way, I can just replicate and 
 repurpose everything I've already built 
 for the past six to seven months on my 
 own desktop in terms of full 
 infrastructure. So you get to use your 
 existing cloud code, your existing plan. 
 You don't have to pay for any form of 
 API if you don't want to. And you can 
 use it because it's literally using the 
 one on your local computer using their 
 bridge, not some third parties. And the 
 beauty obviously is as soon as you set 
 it up, your telegram or whatever 
 interface you choose has instant access 
 to the powerful harness of cloud code 
 because if you just use the anthropic 
 API, you get the intelligence of the 
 model. So you can basically dial up and 
 call your favorite model, however smart 
 it is, and it will give you smart 
 answers. But then you have to create the 
 infrastructure and system to break that 
 down and execute any tool calls and do 
 everything it needs to do. With the 
 agent SDK, you basically have a mini 
 version, a subprocess of cloud code 
 running at all times. So anytime you 
 ping from Telegram, it goes and executes 
 it. So the process end to end looks as 
 follows. In stage one, you have 
 Telegram. This pings over to the 
 Telegram API. This authenticates and 
 makes sure it's you. Then you have a 
 media handler. In this case, if I send a 
 video, if I send a photo, if I send a 
 voice note, this is handled. And in 
 stage five, we have memory injection. 
 And this is where we take the most 
 recent memories that you can see right 
 here that live locally on my computer in 
 a SQL light, which is free to run. No 
 superbase, no convex, nothing. And I can 
 store all the memories from our 
 conversations right here. So if I click 
 on browse data, you'll see that these 
 are all the messages that I've sent in 
 the past couple hours. Once the stage is 
 set, pun intended, we then have the 
 agent SDK, the most important part of 
 the process, implement what's called a 
 claude subprocess to essentially write 
 the word claude in your terminal and 
 then execute your command. And beyond 
 that, it's all about taking the response 
 from our existing claude code instance 
 and then converts it into either text or 
 voice, whatever you want, and sends it 
 back to your Telegram. So, you go from 
 one message to eight different stages in 
 less than 5 seconds. So before we pop 
 into the terminal and I walk you through 
 the mega prompt that I've put together, 
 I'm going to show you the memory system 
 very quickly. So it's composed of three 
 different layers. So layer one is 
 triggered whenever you send that first 
 message and it spawns a brand new 
 conversation and that conversation has 
 what's called a session ID. If we take a 
 peek at my existing terminal right here, 
 you'll see that all of these messages 
 are occurring as a part of the exact 
 same session ID, which allows us to 
 persist context across it. Now naturally 
 by doing this you're not breaking the 
 laws of physics. So you're still subject 
 to the context window of cloud code on 
 your computer which is why using this in 
 combination with the million context 
 window from the sonnet model is probably 
 the biggest cheat code. But let's say 
 that's overkill for your particular use 
 case. Then we have layer 2 which is a 
 combination of SQLite a free database 
 that can run on your local computer 
 irrespective of your OS combined with a 
 version of memory. So we have semantic 
 memory which is a version of vector 
 database based memory. Then we have 
 episodic memory. So conversations can 
 decay over time. So I could have a 
 conversation back and forth and then the 
 waiting of the most recent messages are 
 much higher than prior messages. Now I 
 tinkered back and forth until I got to 
 my sweet spot. But all you'd have to do 
 is follow the steps that I'll walk you 
 through in this video and then you'll be 
 able to decide what is the perfect 
 version of memory for you. Or you can 
 nuke this completely and build your own 
 version. And last but not least, we have 
 layer three, which is context injection. 
 So before every message, we're searching 
 recent memories, the top memories. We're 
 dduplicating the conversation for 
 anything that seems to be noise to keep 
 things as fluid and buttery as possible. 
 So with that, let's hop into the 
 terminal as promised. And you'll see 
 right here that I have a series of 
 repos. And if you've watched my prior 
 videos, then you'll know that a couple 
 of the experiments that I ran involved 
 cloning existing open- source repos 
 including OpenClaw to create my own 
 shopping list of the features that I 
 wanted. And this project started along 
 the same lines except I took it a 
 completely different direction. So if we 
 click on this folder and then we open 
 this rebuild prompt right here and I 
 click on reveal and finder and I open it 
 up right here, you will see that this is 
 indeed a behemoth. I'm not going to walk 
 you through the whole prompt because as 
 promised, it is a mega prompt. And the 
 way I designed this prompt is if you 
 just tag it, you don't even have to copy 
 paste it. It should be able to explain 
 how Claude Claw works, ask you for your 
 preferences, push back on you to see 
 what it is that you're trying to create 
 to make sure that you can create your 
 own tailored version. I did my best to 
 take all the scars from my journey of 
 building it myself and inject it in 
 here. So if you do have a FAQ or a 
 question in general that hopefully it's 
 covered in here. So the TLDDR of this 
 document is it tells you what Claude 
 Claw is, what you can do with it and 
 what you can do with it when it's 
 running, what the steps involve, what 
 does it cost to run depending on the 
 infrastructure. So for myself I'm using 
 Grock with a Q for voice notes just 
 because it's a lot faster than 11 Labs. 
 But if you want to use a clone voice, 
 then 11 Labs is the best thing to do 
 there. And then we have criteria for the 
 knowledge base, session resumption, how 
 the memory system should work when it's 
 full. So all the micro behaviors. And if 
 you want to connect your telegram to 
 your WhatsApp, then these are the steps 
 that you could use to replicate it. And 
 in terms of cron jobs, which is one of 
 the major features that people love 
 about OpenClaw, the proactiveness per 
 se, which is basically a series of cron 
 jobs that run on your computer. This can 
 create a scheduler created by Claude 
 Code to stay on your computer. 
 Obviously, to make this all work and 
 make it persist, your computer has to be 
 on or your Mac Mini. And then I've 
 designed the rest of this prompt to 
 pretty much interview you on every 
 single thing that you care about. So, 
 all you have to do is open your 
 beautiful Cloud Code and do at rebuild 
 and then just say execute this or 
 whatever you want, read this or do 
 whatever is in this, any permutation of 
 that. And then it should go through and 
 go through the essentially this wizard 
 that I've compacted in markdown. So once 
 it runs it, you should get this little 
 ASR animation here. I called it clawed 
 claw light because it's not my version 
 of it. It's a general vanilla version of 
 it. And then it goes through the 
 assistant. It tells you exactly what's 
 involved, the steps like you would have 
 seen in the prompt. So now you can ask 
 questions. You can say, "Help me set 
 this up now." And then it should go and 
 invoke the wizard. And behind the 
 scenes, I've asked it to invoke the ask 
 user input tool to basically pop up this 
 multiple choice to make it as 
 interactive as possible and not 
 intimidating for you non-technical folks 
 out there. For voice, in case you want 
 to send and receive voice notes, you can 
 choose from Grock, OpenAI, 11 Labs, no 
 voice or add your own by going to type 
 something. In my case, I could say Grock 
 and then we click on enter. Next, what 
 kind of memory system do you want? So in 
 this case I have my own version that 
 I've bestowed upon you the episodic plus 
 semantic but you can create your entire 
 different version or you can just walk 
 through factory settings build it see if 
 it works for you and then just iterate 
 as needed then you click on full memory 
 then you want to basically say what 
 features you want to enable souler maybe 
 you don't care about the video analysis 
 or WhatsApp bridge and background 
 service and you say submit and then you 
 click submit right here then it starts 
 the entire entire process for you. Now, 
 in my case, it's about to overwrite 
 everything that I've done. So, I'm going 
 to escape for now because it's going to 
 start asking me very tailored questions 
 cuz all of this is already on my 
 computer. But, it should go back and 
 forth with you. And you should have more 
 than enough to go through. And honestly, 
 I did this from scratch in around an 
 hour or two. And my prompts weren't very 
 impressive outside of the first initial 
 message telling it, I have a dream to 
 use Claude Code with my Telegram and not 
 break terms of service. Once you have it 
 installed, ideally you should be able to 
 execute a command like Claudeclaw and 
 then start the onboarding process and 
 you get a beautiful Aski art like this, 
 the full-blown version of Claudeclaw. 
 Then you can go down the wizard. You can 
 click on yes to continue. And then you 
 can say, do you want voice input? You 
 can say yes. Do you want this? Yes. 
 Video analysis, I can say no. And then 
 WhatsApp, I can say no. Do you want to 
 clone any of the repos? So in this case, 
 I just give you the ability to do what I 
 did. If you want to be able to shop 
 different repos for different features 
 you like, it's a part of the wizard as 
 well. So I can click on no and I can 
 click on no as well. Then it will ask 
 you for either an API key or to ooth 
 using your existing anthropic cloud code 
 max plan. So the TLDDR of this process 
 is you just take the mega prompt, you 
 are posed with those four questions, 
 then you can go back and forth and 
 intervene. You have it get built. It can 
 take anywhere between 10 to 30 minutes 
 for it to get built depending on what 
 the nuances are in your version. And the 
 best part of this is unlike OpenCloud 
 where you have to always worry about 
 maintaining two different brains. One 
 for your desktop and one for on the- go, 
 you have one unified system, one unified 
 AI operating system where you can go 
 through this iteration process. So as 
 you improve your cloud code system in 
 general, your ecosystem, you improve 
 your skills and you make those skills 
 global. So all projects can take 
 advantage of them, then your skills get 
 better, your phone experience gets 
 better on Telegram. You can use it from 
 anywhere. You can point to it, you can 
 use it on a Mac Mini, you can change 
 everything into a different 
 infrastructure so long as you have all 
 those core things in place. And the last 
 thing I'll say on this is despite me 
 using cloud code in this video 
 technically any language model that has 
 a command line interface CLI like codeex 
 like Gemini can be used instead of this. 
 So you could swap the entire process 
 with whatever you want. So if you love 
 codecs then absolutely go build your own 
 version of codeexclaw. And that's pretty 
 much it. So hopefully this is as 
 exciting for you as it was for me cuz 
 now you can get real leverage over 
 building one system incredibly well. And 
 like I said, I'm going to make available 
 the mega prompt that I showed you in 
 this video in the second link in the 
 description below. And naturally, if you 
 want to be able to copy my exact setup, 
 get a deeper dive on all the nuts and 
 bolts on how this works and take 
 advantage of all the features that I'm 
 naturally incentivized to add to this to 
 make this amazing, then check out the 
 first link in the description below, and 
 maybe I'll see you in my early adopters 
 community. And for the rest of you, if 
 you enjoy this video, if you found it 
 helpful, if you like the way I teach, I 
 would super appreciate if you could 
 leave a like and a comment on the video. 
 It really helps the reach and it helps 
 the channel, so I'd really appreciate 
 it. I'll see you the next one.




 0:00 Alright, so the Hacker Glasses are coming on because we're done V1 of Clawd Claw, and I'm going to go through what the onboarding looks like, but let me actually show you the current product.
0:12 I'm not going to say finished product, but the current product. So, this can do pretty much anything that OpenClaw could do as well, except everything lives natively on your computer.
0:21 So, anything that I have, let's say my fine-tuned instrument. NanoBananaSkill, that makes images just like these, instructional ones. I can run this from Telegram.
0:30 I can send an actual video, so I can literally take this out, and let's do something different from the actual video itself, my YouTube video.
0:38 If I just hold this, and I'm explaining to every beautiful person in the community on what Clawd Claw is and how it works, and then I send this video.
0:48 It's sent over, this should be able to go and invoke, basically behind the scenes, my Gemini video understanding, which is through the Gemini skill.
0:57 And you have the ping running on the left-hand side. This is my specific session ID right here. This session ID is what basically correlates to an individual chat.
1:08 So long as you have the same session ID, you're in the same context window. video. So, until next I'm going to just pause until we get back to the response.
1:15 Alright, and it says, you're recording content for the community, explaining what Clawed Claw is and how it works. And then, in this case, I've made it so if I send a voice note, it responds via text, unless I tell it in the voice note to respond to me.
1:28 So if I say, okay, so I want to be able to explain to everyone what are the main commands that they can use with you.
1:37 So I know there's one around ConvoLife, a very lazy command I put together, but what are the other ones? I'm forgetting all of them.
1:43 Can you just, like, list them all out and explain exactly how they work? So, in this case, it should come back with a text response.
1:51 When I resend a different version with my voice, it should come back with a voice response. Alright, so you can see here, it comes back with ConvoLife.
2:00 So, I just send this over to see how much context left, sorry, context window is left in the window. One expert tip is, if it is within, you know, financial means for you, running this on 1,000,000 SONNET, which uses extra usage, so you'd have to enable slash extra usage, then log into your account, 
2:19 then put 10 or 15 bucks. If you want to go that far, then you can obviously keep the context window.
2:24 A lot longer than the normal cloud code. But, uhm, if not, you can still run this on SONNET, or even haiku, because as long as you have everything readily available on your computer, it should work just fine.
2:36 I have another one that's called Checkpoint, where, if I'm nervous, obviously, as I progress this and keep making this better, this should be somewhat automatic.
2:44 But if I assume I'm pretty deep into the context window, I'll just do Checkpoint to make sure that, The last couple of things we talked about really survives and it creates basically a compaction note.
2:55 So, if we start the next conversation, it should be auto-injected in the next chat. So, then we have the normal stuff.
3:01 So, voice notes, like I said, I'll demo that for you as well. I can send over images. Obviously, you can tell I can send over videos.
3:07 So can you. And the date. All of those multimodal functionalities are coming together. Coming from just me making the Gemini skill global.
3:16 And if you're still not familiar with the Gemini skill, if you go to Gemini skills right here. So, Gemini skills, Gemini API dev, skill.md, then you'll see this beautiful thing.
3:27 So, text generation, multimodal understanding, structured outputs, um, context next caching. Out of the models. Now, it doesn't have access to, I think, Gemini 3.1 yet.
3:42 But, in my opinion, it's a pretty horrific model, for the most part. So, you wouldn't want to use it per se.
3:49 And if we go back, let me just do this. If I send over, let's say, uh, convo life, okay, this should come back to me with a little update on context window.
4:00 And, And you can see here, I have obviously my skills. These are the skills of my actual laptop. Then you might have my contact creation skills as well.
4:10 And then, it's just doing some calculations. There we go, context window, 54% used, 92,000 remaining. Now, I'm using, again, the million, so I've been ramming it all day.
4:22 And then, beyond that, we have, you know, let's do another party trick. ause . Okay, so I want you to respond to me via voice note, but I want you to explain to me how AI works in one sentence.
4:33 So, I'm just going to send this over. It should be able, it's using behind the scenes grok with a Q, not, uh, Elon Musk's grok.
4:40 I'm using grok with a Q just because it's super fast. So, it goes, it handles the text of speech, transcribes it back, and it should come back with a, verbal response with a pretty poor clone that I made on 11 labs of someone's voice, but it should come back momentarily with the voice note.
4:59 And there you go, because it had the trigger words in the transcript that comes back. Not sure if you'll be able to hear this, but I make sure it also transcribes what it says.
5:07 So, AI works by learning patterns for massive amounts of data than using those patterns. I'm pausing just in case you can't hear that, but it says AI learns from patterns, So, that's all the, the party trick stuff, and the best part is everything that I can do.
5:18 So, if I have Obsidian running on my computer, which I've been really pushing for a while, a lot of you have been keeping tabs on me, keeping tabs on it, if I do something like Slash to do, I'm gonna have to block my to-do list because there's some private stuff there.
5:32 I'll at least show you what the output looks like. Alright, so I finally- blocked out everything that's not- not sensitive.
5:40 Umm, you can see here, I have my Berlin to-do list. Obviously, we're working hard on that. I have my assistant also helping me with some venues because a couple ghosts at us.
5:49 But that's an example of it actually executing a command on my computer. And I could do similar with other commands.
5:54 So, I have something here called, uh, my LinkedIn post. So, I do execute slash LinkedIn. Thank you. And it helps me go back and forth and turn a video into a brand new conversation and turn it into an actual post with some images associated based on the video.
6:11 So, based on that, I'm not going to go back to that screen. I can now walk you through really quickly the repo itself.
6:17 Alright. So, I designed this. Again, there's no such thing as perfection. I'm sure some of you might clone this and you tell me that there's a bug.
6:23 Unlike other systems in the community. community. where I give you the Eddy 80 and then you do the 20. It's in my best interest to make this awesome because I'm using this already every day for the last few days.
6:33 I love it. I'm not going back to anything else. I don't care what comes out. I'll just change the models maybe.
6:38 But, um, there's a full onboarding flow right here on steps one to step eight. But realistically, I tried to make it as simple as possible.
6:48 So, in your term. . . . So, if you were to pull up your terminal and everything was set up and good to go after you clone repo.
6:57 When you run cloud flaw, you should get this beautiful cloud claw right here and then you can click on yes continue and then it asks you do you want voice input.
7:06 You can say yes. Do you want, uh, there you go voice output. Yes video analysis. Yes WhatsApp bridge. Now WhatsApp, the way I've designed it is I can actually control my WhatsApp through my computer app store app through telegram.
7:22 90% of you, 99% of you don't need that. But for me, sometimes I have some business contacts on WhatsApp where I want to send a voice note and I want to take it, cut it up into different sub messages and lowercase and then send that all over to my business contacts.
7:36 So that to me is help. So that's for you, might not be helpful. If you want to clone the existing repos and you want to shop those existing repos, then you can do that as well.
7:45 Okay. Umm, so I'll do that now. I'll do no. Uh, do you want to update and create a Cloud MD?
7:51 No. By default, it's anticipating that you're going to use your Cloud authentication. If you want to add an API key instead of off, then you can do so as well.
7:59 Um, this is auto-star- Mac OS. I've begged Cloud code to make this friendly on Windows. Let me know. I will never know if it's going to work really well on it.
8:08 Um, until you actually come back to me. I have, again, invested interest to make this awesome. So keep using this thread of this post for any bugs or even feature requests that are reasonable.
8:19 Um, in this case, I'm just going to do no. And I just said no. And that's why it's going to terminate everything because it didn't give it permission.
8:25 But if, for whatever reason, it's not working, let me know. Um, alternatives, you can just clone the repo and follow the steps we have right here.
8:35 And it'll tell you what you need, how to set up the telegram bot, assuming you want to use telegram. You should be able to reroute this elsewhere.
8:42 Uh, once you clone and install it, you just have to do CD, install, NPM, install, uh, Cloudclaw. And then beyond that, that.
8:49 All you have to do is, if you're stuck, just use what I use, warp. So all I do, is go to warp, generous free tier, you can do agent, okay, slash agent.
9:00 Once you're in a slash agent, uh, conversation. Then, ooh, let me just make this work. There we go. Once you're in this kind of conversation, you can ask whatever you want.
9:10 So you can clone the repo and be like, what the heck is happening with this? How do I configure it?
9:13 All right. How do I change this, et cetera? And then you have your telegram ID and everything else that you'd need.
9:19 So we, this goes through how it works, uh, what's included, what's not included, everything you need. Default behaviors, what's up, how it would work behind the scenes, how memory works and how you can configure it.
9:32 And yeah, everything you'd need beyond that. So this is V1 and you have the entire architecture right here as well.
9:38 So everything I've taken a scan at, obviously we're going to ameliorate this, we're going to make this infinitely better, but I'm excited to finally give this to you.




00:00 So in this video, I'm going to walk you through the current state of the Clawed Claw system. And I'm going to walk you through some tips and tricks.
00:08 Some of you asked how can you create effective skills. I'll also show you that in this video. And, one thing I want to draw your attention to is the repo.
00:17 Now, I already linked this on the V1 post, but you want to make sure that you're watching it. No one's watching it.
00:22 The reason why I want you to watch it is I'm almost done. People is cooking now. You can see I've done committing an hour ago.
00:28 I am ever evolving and improving the system because, like I said, I have a vested interest to make this awesome.
00:35 So if you go to the bottom, for example, these are some additional slash commands that I have. So now I have a brand new slash command that's called respin.
00:44 So, if you start a new chat because your context window has flooded, then restart the respin will go through whatever database you've connected.
00:51 In my case, it's just a SQLite database, but we'll get to that shortly. And then it will onboard itself on the last 20 exchanges.
00:58 And then we have things like slash slack where I've also added a slack skill and the slash slack ability to actually interact with a bot.
01:08 And if we go down here, you can see this is slash new chat. Slash respin, if you want to interact with slack very directly, you can.
01:18 And then if you just feed this repo, if you just reclone or you update your version of the cloned repo and you won't really have your own thing going, I don't want you to have to refresh and redo everything.
01:29 You can just clone it, ask Cloud Code to go through any changes, any new steps that you don't have in yours.
01:34 And if you want to, for example, add this slack capability that I have right now, I made sure that I could document every single step of what you would need.
01:44 So just give this to Cloud Code. It will tell you what to do. In my case, I was so lazy that I had to use agent browser to open my slack app, authenticate, go to the right tab, use the right tokens, set up all the right commands so I can just easily go on my phone on Telegram, be like, Hey, can you send
02:01 this to my, YouTube editing team? Ask them for X, tell them if we can turn it around in two hours, et cetera, and it can do it.
02:08 So this gives you the step-by-step. Anyway, this was all just to make sure that you know that your friend here is going to consistently be cooking.
02:17 I improved memory, just general competence of my friends during conversation back and forth. Anyway, so let's get to the brass tacks.
02:29 So if you're here and you're watching this, then I would assume, you know, what Claude Claude is from my video.
02:34 And the TLDR is you can use your phone to interact with your existing stack and ecosystem on your desktop. Only prerequisites is a phone app.
02:45 In my case, it's I use Telegram just because it's the only app that I have where I have nothing else that is, compromising and I can't send something wrong to the wrong person.
02:55 Now you can use the Claude app and I know the remote control came out. One thing I will say right away with the remote control, it is awesome for terminal based commands in project folders, in plain English.
03:08 What I have here is has access to my entire computer through the world of Claude. So, any folder, anything, can move files, can, anything I want, it can do.
03:19 It can open an agent browser, spin it up, access any skill. The way that they've released remote control is if I'm in a specific folder, so let's say I grab, let's say a new tab here, later.
03:33 Bye. I want to show you what I'm working on, on YouTube, but let's say this is my YouTube command center.
03:37 Now, my YouTube command center is absolutely devastating in terms of how much I produce. So everything you see on YouTube from banners, to ExcelaDraw files, to Gumroad, to Gumroad our competitors here.
03:58 it's called slash video launch. So once I'm ready to go, we cook. It would make absolute sense for me to use remote control here, because I want everything to happen contextually aware with the project-specific context and the project-specific skills.
04:15 So remote, to me, is not a replacement. It is a beautiful compliment. Okay? And just to rejig your memory. So you type question, Telegram delivers it, Clawed Claw checks its memories if it needs to, runs on your Mac or Windows, and you see the answer.
04:31 And then as you have back and forths, it will always go back and go through that loop. And what do you need?
04:38 You don't need Telegram if you don't want it. You can swap this out. I would just say WhatsApp is really annoying if you want to set it up.
04:44 And probably the it. The least secure from what I've seen, but you can use Slack right now. I can, I made it so I can also interact with it from Slack if I need to.
04:52 You need a laptop and, that's pretty much it. And now I have Grok behind the scenes for voice input for speed, but you can use 11 labs.
04:59 You can use mini Macs. You can use whatever you want. Okay. Now, if we go into the next section, how memory works, a few of you, a few of you, rather have asked me how that works.
05:10 So layer one, we just talked about, you're basically just having a back and forth. It's just continuing the context until the context is, filled up.
05:18 So you're basically just using a normal terminal. The same way Claude already has an agentic harness that's capable of carrying that conversation forward.
05:25 We're doing the exact same thing here. Then we have long-term memory where in the SQL lite database, they would have seen, before I have a series of things being stored.
05:35 I'm now storing a new update is logs. So anything that's happening in the course of the conversation. So all of this is being stored in case I ever have an error.
05:45 I can then open a brand new version of Claude and you can see here, I got an error earlier today when I was testing the Slack integration.
05:51 And then all I did was just copy this, initially. And I said, listen, I don't want to copy this anymore.
05:55 I want you to store the logs. So then I have the log stored somewhere. You can customize this the way you want.
06:02 I just have a version out of the box that you can use. I love SQLite because it's free. And for most of things that I'm going to be thinking about here, like I'm not storing multimedia files.
06:12 There's nothing too crazy. It's very text-based. So it's good for lightweight. And then layer three, your skills and personality. Now, some of you might still want your soul.md for OpenClaw, but I can assure you that a whole essay about personality and values can be compressed into three sentences where
06:31 the AI can extrapolate what you mean in a CloudMB file. I can guarantee it. If you want to add a soul.md, be my guest.
06:41 Now, how memories are created. So when you say something to ClawdClaw, if it appears to be an important memory, obviously this is in alpha slash early beta.
06:51 Like, I prefer that. Remember this. I always do this. Then it should store it in long-term storage. This does decay.
06:59 So 2% waiting per day. If you don't want it to fade, then you just have to be mindful that if it recalls everything, let's say, four months from now, you're going to have a problem because there's no way to sift through that.
07:11 Then you have short-term memory, which is short storage. Like, summarize this article, what's the weather, send that file, take the Fireflies meeting, etc.
07:19 So, this is fully customizable. And here, just to make sure that you are equipped with everything you need, let me move to the right tab here.
07:26 Sorry. This is the one. You can literally open, a brand new terminal in Cloud Code. And you can say, I want to make all these changes to my instance of Cloud Claw.
07:40 Okay? And we're at a point right now where if you run Opus long enough on a particular task, you should be able to edit it, to make it do your bidding, to switch my memory, to switch the way personality is, distributed and exhibited.
07:53 All of this is under your control. I added Slack today just by asking it through the most horrifically phrased prompts.
08:01 So just some more information about memory decay, how forgetting works. So if I say like, I prefer bullets every time I mention it, it gets a boost.
08:11 So if I mentioned it, it gets a boost. So there's a longer time horizon for survivability. of said memory. Again, this is conceptually what I'm going after.
08:21 In execution, I still see some flaws, so I'm going to keep improving it. In my case, after, if I never mention anything again after X amount of days, then we get to the death line, where it's automatically cleaned up.
08:34 It's kind of gone until I bring it up again. For you, it might make sense that you persist a brand new memory.
08:41 So with every message, if I say, like, what is my Calendly link? It will go and search. I have a skill now that I've made.
08:49 Again, really cool thing. I want to, I'm going to change your life. No, your mindset. We lived in a world where if any of them told you this is the six things you could do, those are the six things you would do.
09:00 If Zapier says these are the eight things you could do, you can't do anything beyond that. Even though the API allows you to do more.
09:08 And that was the realization I had recently, the light bulb moment that I'm going really deep in, where I can just feed the raw API.
09:15 And I want to show you an example shortly of any service. And I can do whatever I want, as long as the endpoint exists.
09:23 Sometimes I can do things that aren't in the endpoint, but that's a more advanced topic. Now, once you've Once you do that, it will go and search this memory, see if it has any form of memory context, and then Cloud sees the context plus the message, and then responds accurately.
09:39 It's like a very, very light version of RAG. It's not RAG, but a light version of RAG. Semantic. So memory in action.
09:47 So I always prefer a short bullet, responses, no fluff. So this should be stored in long-term memory. Thank you. At strength number, at strength one.
09:56 Day three, what did I ask you about last Tuesday? So memory found, it should be synthetically boosted. Okay. I'm going to keep disclosing this.
10:04 This is still not perfect in actuality. The concept I think is awesome, but when I test it out, once in a while, I'm happily surprised so far, it's been what, five days or four days, but it still needs some work.
10:16 So the database under the hood is running. Everything again on SQL lite, you can literally go install SQL lite browser, download this bad boy on your windows and or normal desktop.
10:28 And then it is so straightforward to use. Once you open the database, you're good to go and you have everything you need to navigate.
10:37 See what you need to see. If you want to use SuperBass, Convex, be my guest. If you want to use AWS, also be my guest.
10:46 This is meant to be malleable. You don't have to do it my way. Now, section three, the moving parts. What, what actually happens behind the scenes is the real cloud code is running on your computer.
10:57 And I just want to reemphasize this multiple times because some of you have asked me, could you please add a feature to enable agents?
11:05 And I'm like, instantly. It already exists because usually you're using cloud. So if you want to offload a task for sub-agents, you can just ask for that.
11:13 The only tricky part here, this is the part where I come in, right, as I keep experimenting, is if agents are running, let's say sub-agents, not agent teams, they can take five to ten minutes, right?
11:26 So in the whole time, do you want the word typing on your chat? Or do you want some form of status updates, in, in the middle?
11:34 So we would do what's called polling. And if you've ever used end-to-end, you know, there's a polling thing that tells you how long should I wait, to retry and what's happening in the meantime.
11:42 So you just have to configure polling, but everything you want is already accessible on your device. So skills are not built in.
11:50 I did that for a very intentional reason. One, my skills are mine, meaning like everything that I customize is structured to the way I work.
11:58 Okay. But just to make it easy for you, I've also made some boilerplate versions of the ones that I've created available to you in the repo.
12:06 So this is the one I made today for Slack. It's a Slack skill. It has everything that you should need to be able to interact with your Slack.
12:15 And for the slash command, this is how it gets all the paths to interact with. And obviously I have in the repo on the README itself how to configure it.
12:25 So I've tried to insulate your need to look elsewhere. And once you decide on your skills on your computer, I strongly recommend you never clone someone else's skills.
12:35 Now, in my case, I hope you can trust me. There's nothing malicious in there. You can take a look at it.
12:40 But if you go to somewhere like Reddit, like awesome skills or skill marketplaces, please do not clone skills as is from non-official providers.
12:49 Non-official meaning not Gemini, non-anthropic and not OpenAI. I don't even know if they have skills. They have a skill issue.
12:58 There you go. Pun intended. One skill that will enable tons of functionality. I might have already alluded to this in a video.
13:05 Is Gemini skill. The reason why this is awesome is now you can leverage all of these from one singular skill.
13:13 So once you enter your API key in an environment file .env, then you should be able to leverage all of these in tandem.
13:19 So that's where I was able to send a video of myself and have it understood. I was able to ask it to create a diagram and it would use NanoBanana.
13:26 Now we just got apparently NanoBanana 2. So all of this is comes from one skill. So I recommend you create and use high leverage skills.
13:34 Don't clone someone else's skill. Look at their skill. Copy paste the text as you see it. Don't import it. Paste it into Cloud.
13:43 Say I want to use this skill for this thing. Let's recreate our own version. Don't trust external skills. There's tons of now HTML injection and there's a lot of people falling prey to it.
13:53 And I don't want any member of this beautiful community to be a victim of that. Now, I am pro CloudMD.
14:00 So my CloudMD looks like this. So who is Mark? How to respond. That's the tone. For me, I don't need very spiritual values.
14:09 I don't need essays on introspection. I just say, talk to me in lowercase, no emojis, no sycophancy, when I see you.
14:17 When I say yo, I want you to say yo, just match my energy, mirror me. What you can do, so I just, always informative with the skills it has and how to use them, and any guardrails.
14:30 So example, two days ago when I first implemented the Gmail skill, which is not a normal skill, It basically sent emails without asking me if it's cool, like what do whatever it wrote.
14:42 So a couple victims got AI generated emails with like four M-dashes, and it made me internally cry inside. So I have a rules and boundaries section right here, okay?
14:53 Now I have the voice to text, you can also leverage the Gemini skill. There is, TTS in the Gemini skill, there should be.
15:00 I'm using Grok for speed, but you can use, again, whatever you want. The one thing that I have in my repo, which is helpful if you want to be able to adapt it to whatever you're building, is when I tell it in the voice note, respond to me via voice note, it will do that.
15:16 Or right now, I was on my way to a meeting that my Clawed Claw happily helped me create a brief for in a pricing sheet because I had no time and did due diligence and sent me a voice note while I was in the shower, and I auto-ployed it.
15:29 And it just closed a new, workshop deal, which was awesome. But, as more show to just to show you the power of it, I have a fascination with this because it's actually deriving business value.
15:40 Finally, with OpenClaw, I had to do open heart surgery, pun intended again, to make it do what I wanted it to do and spend tons of tokens.
15:50 The repo's clean, it's very readable, and you can just ask Opus, go to Mark's repo, go look at his latest update, let's snag this thing, don't worry about this other feature.
16:00 Okay? Now, WhatsApp, a couple of you DM'd me about it. This is a very insecure version of using my WhatsApp.
16:08 I have a business use case that's very helpful for me, so I'm actively trying to find a way to make it more secure.
16:13 But this is probably the most insecure version. Insecure part of my implementation. So, very few of you would have a legitimate use case of using Telegram to respond to your WhatsApp.
16:23 For me, I had a couple of different reasons, more personal, that made sense for me to do that. Now, the scheduler.
16:29 This is the thing that you guys ask me. Yes, but how do we replicate this beautiful behavior that we get from OpenClaw, where it's proactive, it has emergent behavior?
16:38 One, that emergent behavior many times was hallucination. So, you're basically seeing hallucination of a language model being anthropomorphized through an assistant and mistaking it for emergent behavior.
16:51 And by the way, for the first day or two when I used OpenClaw, I thought I was witnessing something new until I went under the hood and I'm like, oh, this was a misfire.
17:00 This is not intelligence. So, thank you. The scheduler creates cron jobs and the beauty is Clawd is attached to your computer.
17:08 Clawd uses Bash, which allows it to interact with your system controls. So, if you say, create a schedule every morning, I can show you right now if I pause right here, it goes through, gives me my day, my TLDR of exactly what's going to be happening, and I can tell it to do some research right here,
17:25 and then send me a voice note with a little background on everyone I'll be speaking to, any paid consult, etc.
17:30 So, this is a game changer. So, that is the scheduling part. And then we get to the penultimate. I believe it's the penultimate.
17:38 Penultimate means second last, by the way. Let me just make sure this is unfuzzy. Let me just defuzzy this. There we go.
17:47 Security Architecture. So, it's basically the, I call it the bouncer model. If someone discovers your bot's name, they can't use it.
17:54 When I first published this, before you had access to it, the morning of my YouTube video, I was doing a security audit of my own repo, and I noticed that if I did a slash command, like slash new chat, when I did the audit, it's like, oh, this is a huge vulnerability.
18:12 If someone messages your bot, and they know the username of your bot, and they message new chat, or slash context, they would be able to retrieve responses from your Telegram bot.
18:22 So, to me, I was like, okay, that's horrific. But, it's just a good conversation to have, make sure you still audit it, just because mine said, okay, these are the only two critical, doesn't mean that yours won't have the same, right?
18:34 Language models are language models, end of the day. Now, in this case, when it comes to, is this legitimate, I still, I'm not a lawyer, this is not legal advice, okay?
18:44 I'm going to make that well established. I have yet to see, and meet, someone whose account was actually banned for OpenClaw.
18:53 It said it would get banned, but I've yet to actually meet that person. So enforcement is different from what's written on paper, and if you go into, let me just put, I can pull this up, let me give you a second here.
19:09 This is one of the fundamental tweets that got me confused. So during the most recent debacle on OpenClaw, they said they would ban everyone's account who's using it.
19:18 Then they released this apology saying, nothing's changing about how you can use Agent SDK in Mac subscriptions. And then we get to this tweet.
19:26 So we want to encourage, encourage local development and experimentation with the Agent SDK in CloudP. This is literally what we're doing with a 200 line of the TypeScript that make this possible.
19:38 So if you're building a business on top of Agent SDK, you should use API key. Now, look at these words here.
19:45 Again, I'm going to say that for the nth time. Not a lawyer, not legal advice. Should is a directional, not a definitive.
19:55 And also, I'm not building a business. I doubt you works here. It's for personal usage, so local development and ex- next Experimentation, this is me experimenting.
20:03 So I can't give you a definitive statement on that. I can just say that we're using anthropics architecture to access our own infrastructure using their own bridge to our own plan.
20:17 I've read the TOS so I can, I can see what verbatim says. It says there's no interactions. what's whatever. Amazing.
20:24 But, you know, Nana Banana said you can't also make logos and you can't recreate things that already exist and people do it all the time.
20:30 So again, not legal advice, enforcement versus a written policy and this from their own team, right? Their own cloud code team.
20:40 It throws a wrench in there. So for me, I can't give you a definitive statement. Don't want to mislead you.
20:46 Thank you. As soon as I see this evolving, I will pivot if needed and I will obviously make sure to let you know right away.
20:54 But I personally don't see something at this time that tells me this is horrific for us to do. so in terms of where your data lives, so telegram, cloud, it kind of just roots messages.
21:04 It doesn't actually store them if you don't want it to store it. And then in terms of- of your Mac or your, obviously, I'm not being discriminatory here.
21:12 You're beautiful windows, you're beautiful Linux. Everything- important stays on your computer. You have a dot cloud that has all your settings.
21:19 This is where all your global stuff is, your MCPs, your skills, et cetera. And then you have a dot-env. This is where I recommend that you put all- everything that is worth sharing.
21:30 Then you have the cloud, claw, DB. This is where you have- Memories, Sessions, Tasks, et cetera. And then I have a way to transcribe.
21:38 You can use 11 labs if you want. Then the full architecture is you have some input. So this could be text voice, video.
21:46 Ignore this for most use cases. Then you have the cron job. Then you have the clod claw core. So you have the bot, the memory, the agent, the voice.
21:55 Then you have your clod code. So everything that you- You have put in your system and made global. If you don't know how to make a skill global, you take skill that you build, and you ask, can you please make it global?
22:06 Store it at the root level. Thank you. Again, if that doesn't land verbally, I want to show you an example to finish this off as to, how you can make a skill, use the skill, invoke the skill.
22:17 So, let's get to the- the final part here. So, this is just examples of things that I've added. So, respin.
22:26 So, let's say you've been chatting with your agent for a while, and your, paranoid. So, you do this slash command I made that's called new chat, which basically respins up a brand new session.
22:36 then respin can go through your conversation history in your DB to pull up the last back and forth. So, then you basically contact- contact.
22:43 You inject along with the caught MD, right? So, with the context window, under 75%, things will go really well. 75% plus.
22:56 You're in a danger zone, obviously at 100%. Once in a while, you might get a crash. Now, I've made mine crash gracefully.
23:03 In the developer word, developer world rather. When you see- They gracefully? It means it doesn't just collapse. Because mine just said this morning, system error?
23:11 Please check logs. That's it. I have no indication as to what that means. Now it tells me your context full.
23:18 So at least it- when it crashes, it just stops working. So you can make yours work whatever you want. Now Slack, I added that as well.
23:25 Through a combination of a skill and a slash command. All the instructions again No. Are in the readme. Then you have the Mac, then you have a telegram.
23:33 Or your windows and your beautiful Linux. Then all the commands I have are here. Which are in the repo as well.
23:40 So I've already touched on these. this one doesn't fully work right now. from what I've tested. So I'll keep working on it.
23:46 But again, do you have to be, contingent on me? If I add things that seem to be- useful. Again, go and watch the repo itself.
23:54 Then feel free to take that and add it to your stack. Or add it to your own Frankenstein version. So this is the TLDR of the function.
24:02 And let's walk through the creation of a skill. So Gumroad is what I use for resources. Free resources that I put out in the world.
24:11 I have hundreds of products now. they're all free. And they do generally- Great some passive income due to very good Samaritans out there.
24:18 Very kind people to recognize, the hard work that we put here. And I want to be able to interact with it via API.
24:25 Now, if you go into Enidend, and hopefully I can still log into Enidend because I have canceled my subscription. Cause I've moved everything over to some form of custom code job outside of our client stuff.
24:38 Some of that still runs on Enidend, just cause it makes more sense from a visibility and a maintainability standpoint. But I'm trying to open this just to kind of drive the point home.
24:48 So, if I add a step, let's do Gumroad. Gumroad Trigger, okay? okay. So, let's say this is the world that you live in.
24:57 So you can only look at Cans- 7 7 8 8 installations, disputes, dispute ones, refunds, and when you have a sale.
25:03 So imagine your entire world of interacting with Gumroad is limited to this. This is what we had to live with for a while, right?
25:10 So, if it was Fireflies, which took forever to come to Enidend, this is all you could do. Let me move this here, just to drive the point home.
25:18 This is every single action you could do. Okay? And beyond that, you're on your own. So you could get a transcript, but if I wanted just the link to the meeting itself, even though it's available via API, if the action was not made, you're- you're gonna have to make an HTTP request to figure out how 
25:39 to set up the body. That's a huge annoyance, especially if you're building back in the day. So, I just wanted to- do the following, and I kept my session, so it can actually go through it.
25:51 Alright, and part of this is meant to be humorous, just so you don't- your eyes don't glaze over, but go deep and crawl every part of this API, and do what needs to be done to make use of it.
26:00 Our goal is to crystallize knowledge on how to use all the endpoints to create a skill that we can invoke globally.
26:05 Don't be lazy and tap out as soon as you hit errors if you need, clawed and chrome to- see the entire page, so be it.
26:12 If you need to navigate with more firepower, use the Agent Browser skill, which I found out was like broken on my computer.
26:18 Don't come back to me with anything that isn't a positive outcome. Now, this is obviously superfluous. I think it worked though.
26:25 Here's the API. So, I gave it the API, it went, and I can't show you all the back because my API keys are here, so I'm going to fast forward to- the next relevant part.
26:36 So, it took 15 minutes, and it opened my browser. It went on the tab, created a token, stored the token, set up the, the actor, and the OAuth application itself.
26:48 I did nothing. I just let it use Cloud and Chrome, which, by the way, is very inefficient compared to Agent Browser, but it still worked.
26:54 It then came back, gave me a rundown as to what the- Thank still does, okay? And I can access it anywhere with the skill covers, and then I'm like, okay, let's see if it's full of smoke.
27:05 So, let me go down here for a sec, and I said, let's test it by checking how many people downloaded in my latest resource.
27:12 So I'm gonna pause, and I'll go down. And you can see right here, 928 downloads across 81 countries, heavily U.S.
27:19 led, and I asked- Top 5 countries, make this a global skill, it was already a global skill, and you can tell, when it puts it in dot-claud skills, then you have this, then I checked right away, because you don't have to restart your bot, and this is just a skill that exists on your computer, your bot
27:37 interacts with your computer. So everything that's live as a skill or a functionality or as an MCP is accessible via a telegram bot, or whatever interface you've chosen to address.
27:46 So that is how everything works, that's how you can create skills. So if you, one thing I did for Google, because the way Gemini works, let's even via the Zapier MCP, or the Anadn MCP, is your old is limited to something, so I wanted to be able to do things that were in the API, that were not in the 
28:05 actual functionality of the app itself, of the, Anadn MCP version. So, one thing you can do is just go to Gmail, API, Docs, okay?
28:16 All I did, this one wasn't the most straightforward, by the way. It's not like I intervened, but I just gave it the link, and I'm like, I want to make a skill for Gmail, and I want it to be my own.
28:25 So give me instructions on exactly where to go, to give it the secret keys, the credentials, if you ever have used Anadn MCP, and you've on-boarded yourself, on that platform, by creating, you know, your Gmail account, it was very painful the first time.
28:40 That's actually what inspired me. I'm like, okay, Anadn made us go do this. I could probably go do that myself, with Cloud Code, make my own version, and then pythonically create my own skill, and I could probably make it really customizable.
28:54 And this skill's amazing. Like, now that I've been using it for six, Six... Seven days now, it is awesome. And I have this dream that's coming into fruition, where I can open just a black terminal, and I can open my Slack in one terminal, then I can open my, WhatsApp, then I can open my Gmail, then I
29:13 can open my school inbox, cause, I wake up to like 25 messages a day, and I wanna try to stay on top of as many as possible, and I can just go f from one terminal to the next, and just like whisper flow, and just vibe, and not go from one interface to the next, so that's my introverted dream.
29:29 So you can do the exact same thing here, it will walk you through eventually, and it'll say, oh, I don't know how to do this, be like, just double check, whether you can or not.
29:37 Now it can pull up my inbox in a nice pretty table on my mobile, I can tell it go, open these two, go move these two, go schedule this, I then gave it Google counters API, go do the same thing, and now use the credentials that we made for my Google Workspace for the Gmail.
29:53 Now you can get leverage, and I could probably stack on Google Drive too. So the world's your oyster, this stuff is super potent, and this is not a waste of your time, this absolutely blows open claw out of the water, no questions asked.


