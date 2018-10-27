#JS Mobile Conf 2018
https://jsmobileconf.com/
My notes from the conference on the talks I attended

## JS Mobile Conf Day 1 - 10/25/2018

### Keynote - Evolution of the JavaScript Mobile Developer

- Presenter: Todd Anglin - VP Product & Developer Relations at Progress
- Twitter: https://twitter.com/toddanglin

### Talk1 - Responsive Design: Beyond Our Devices

- Presenter: Ethan Marcotte - Independent web designer (Boston based)
- Slides: 
- Twitter: https://twitter.com/beep

Responsive designers now focus on patterns: reusable design modules we stitch together into larger layouts.

Things to check
- Atwood Law
- the teaser - type of design element

```css
.teaser-hed {
  display: flex;
  flex-direction: column-reverse;
}
```

```css`
@supports rule
```
Use the supports rule to check if a specific device supports a functionality as `display: flex:`

`ushahidi` an oss pattern library project

Scott Jehl

> Note to self: find the plugin the presenter used for showing the grid


### Talk 2 - JavaScript ❤️ Binary Data

- Presenter: Kirill Cherkashin - Software Engineer at Firebase
- Slides: https://kirjs.com/binary/0
- Twitter: https://twitter.com/kirjs

colors are 16 bits based, you could also specify colors in 6 bits in some cases.

```javascript
console.log(('1010101').toString(36));
'lol'.charCodeAt(0);
String.fromCharCode(454);
```

big-endian vs little-endian

```javascript
p = new Parser()
  .string('gif', {length: 3})
  .string('version', {length: 3})
  .unint16le('width'
  .unint16le('height')
  .bit1('globalPallette')
```

Proto Buffers 
Flatbuffers

Thrift (apache/facebook)

https://formats.kaitai.io/


### Talk 3 - 1 codebase 3 apps

- Presenter: TJ VanToll - Developer Advocate at Progress
- Slides: 
- Twitter: https://twitter.com/tjvantoll

Web vs Native - opinions
Having a web app, iOS app and Android app

react-native-web on GitHub

The fetch method is implemented in native code

React native uses the same HTML and CSS and ends up with crazy markup on the browser. 
NS has *.tns.css and *.tns.html are definited separately for the web and native

### Talk 4 - Hot Module Replacement in Webpack and NativeScript

- Presenter: Stanimira Vlaeva
- Slides: 
- Twitter: https://twitter.com/StanimiraVlaeva

https://webpack.js.org/concepts/hot-module-replacement/

### Talk 5 - The FaaS and the Serverless

- Presenter: Simon MacDonald - Senior Software Scientist at Adobe
- Slides: https://t.co/as2sQgSBLQ
- Twitter: https://twitter.com/macdonst

Showed us how for a specific app he changed from a heroku hosting to a FaaS


### Talk 6 - Building Rich Offline Applications

- Presenter: Tejas Ranade - Product Manager at Progress
- Slides: 
- Twitter: https://twitter.com/tejasrnd

### Talk 7 Lean Native

- Presenter: Jeff Whelpley - Co-founder and CTO at Swish.com, contributor to Angular, Google Developer Expert
- Slides: 
- Twitter: https://twitter.com/jeffwhelpley

Notes:


## JS Mobile Conf Day 2 - 10/26/2018

### Keynote - Standardizing JavaScript

- Presenter: Jory Burson - Standards Liaison at Bocoup
- Slides: 
- Twitter: https://twitter.com/jorydotcom

She is serving on boards, committees, and working groups for the JS Foundation, Ecma International, and the W3C.
JavaScript's standardization efforts in Ecma TC39 and what it means to create and implement open standards.

Tech description:
- how easy it is to read
- what other specs does it cite

IP policy - have to be done in advance by the legal team

Issuing Authority - what is the company that is publishing

ECMA - the only one that actually agreed to publish JS 🤣 😬 😶
- ECMA has 12 active technical committees and 34 members from various companies
- Anyone can join by just emailing the committee

TC39 accepts proposals in GitHub https://github.com/tc39/proposals

Bocoup has a representative on the TC39 - Leo Balter. 

### Keynote - Building an Innovation Engine Inside Your Organization

- Presenter: Anton Hristov - Director, Emerging Technologies at Progress
- Slides: 
- Twitter: https://twitter.com/AntonHristov

In order to have successful innovation initiative you don't have to "think outside the box". Instead "inside the box":
- time ⏳
- money 💰
- resources 📚
- people 👨‍👩‍👧‍👦
- laws of physics 🚀

Team roles for the win lab:
- Hustler
- Hacker
- Hipster

Success metrics:
- Acquisition
- **Activation**
- **Retention**
- Revenue
- Referal

If a team from the innovation lab is successful, rebrand and merge the product under your portfolio

Books:
- Disciplined entrepreneurship - http://disciplinedentrepreneurship.com/
- The Lean Startup - http://theleanstartup.com/
- Zero to One - zerotoonebook.com
- Business Model Generation - https://strategyzer.com/books/business-model-generation
- Crossing The Chasm - https://www.amazon.com/Crossing-Chasm-3rd-Disruptive-Mainstream/dp/0062292986
- The Innovators's Dilemma - https://www.amazon.com/gp/product/1633691780/ref=dbs_a_def_rwt_bibl_vppi_i1

### Talk 1 - VS Live Share Can Do That?

- Presenter: Burke Holland - Senior Developer Advocate at Microsoft
- Twitter: https://twitter.com/burkeholland

https://burkeknowswords.com/

aka.ms/live-share-pack

```
liveshare.guestapprovalrequired
liveshare.focusedbahaviour
```
>cmatrix

- Code streem 
- use slack inside vscode

what is it good for 
  - workshops
  - setting up someone's machine

### Talk 2 - Building Progressive (Web) Apps

- Presenter: Michael Solati - Front End Engineer at Sellpoints
- Slides: https://medium.com/@MichaelSolati/pwas-with-angular-being-fast-cb3f9d590a93
- Twitter: https://twitter.com/MichaelSolati

Check your app with lighthouse

Addy Osmani about the cost of JavaScript
https://medium.com/@addyosmani/the-cost-of-javascript-in-2018-7d8950fbb5d4


### Talk 3 - Everything you need to Node

- Presenter: Tara Manicsic
- Slides: Developer Advocate at Progress
- Twitter: https://twitter.com/tzmanics

Presenter - @tzmanics
https://twitter.com/Tzmanics

> Interesting mentions: 
  > - Harvard Extension School - you can get regular Harvard courses for $40
  > - Creator of node wanted to have real time push notifications with JS

http://drawwithme.herokuap - doesn't work

1. Node for games - using web sockets
2. Node for Server Side rendering
- Medium Article - operationalizing node.js for server side rendering
- Medium Article - server side rendering with Angular 5+
- Dev.io Article - Parsing JSON with Node.js

https://www.crowdcast.io/e/dshawaf8

3. Node for IoT
- https://tessel.io - really good for beginners
- https://johnny-five.io - build here in Boston at Bocoup

### Talk 4 - Writing docs 

- Presenter: Chris Fritz - Vue.js core team member
- Slides: 
- Twitter: https://twitter.com/chrisvfritz

Before writing docs - make the docs beautiful. Invest in a theme and make them pleasant for you to look at them.

Why do we write docs - people need to know about your feature
> A feature doesn't exist until it's documented

DDD - Documentation Driven Development
Write the docs before writing any code, if it's easy to explain it's gonna be easy to use.

Goal - to manage emotions
people to feel smart, powerful, cause if people are frustraited to stop learning and they *stop*!

Questions to ask when writing docs:
- are people being interupted?
- what do people fear?
- what do people need?
- more... 

If you feel like you are an expert in something you should be teaching it

Emotionally prepare for feedback when writing docs:
  First drafts are **always** bad
  let go of the ego

- have a video for 5 min intros - it's good because people can see it passively
- how does it feel video - 20 t0 30 min
- 80% effectiveness - 1 day

Have references, API listings, examples, cookbooks

maximizes power/effort
- what is going to make your users most powerful - the least amount of energy
- helps decide in what order to introduce efforts
- but there should be one concept at a time, both in test and in code
- be aware of the assumptions that you are making
- tell a story

Don't start with a solution/feature - start with the problem

example: "using props" vs "passing data to child components using props"

avoid humor for intercultural docs

respect people's time - documents have to be good, so that reviewers can help make them great

avoid obsessive perfectionizm

What to do when people are mean to you: 
1. Is everything going to be ok?
  we have to cope
  stop and cry

2. Ask them what the problem is and then set the bounderies of acceptable behaviour

3. How to be frendlier than you are:
  3.1 temperature
  3.2 intensity
  3.3 paced breathing

### Other Resources

- https://testingjavascript.com/
