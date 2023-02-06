0:00
astro is a four times improvement over next js in this example right out of the
0:06
box how cool is that astro 1.0 is here and with it is the opportunity for us as
0:12
next.js developers to reuse the components that we have in nextjs in astro
0:18
but have much more control over what code goes to the client and the result
0:23
is much faster sites it's the island architecture brought to life for react
0:30
right now let's jump right into it
0:37
all right so here's the astro home page and it's got this awesome little call out here
0:43
and it talks about how you have 138kb of javascript going to the client with
0:49
nexjs and the 7.6 kb with astro and the question is does that
0:55
actually result in a faster page so the first thing we're going to do in this video is we're going to actually
1:01
put next js and astro head to head and see how the performance stacks up
1:07
and then hoping that that gets you excited about astro will then go into how to take a
1:13
practical next js application and turn it into an astro app all right so first
1:19
thing to do is look at the app that we are going to use as our testbed so what's happening here is we are taking
1:26
the different types of the pokemon we are then grouping by that type we're then sorting all of the pokemon on that
1:32
particular type and getting the overall number whatever it's just a whole bunch of calculations and it effectively
1:40
represents a load test of these different frameworks okay so let's go over and take a look at the
1:46
source code
1:52
so in the github repository that is linked to in the description this video down below
1:57
there is all of this code is available to you for free as all these videos are and what we're looking at right now is
2:03
the pokemon next static directory and what we're going to do is we're
2:08
going to compare next.js running in static mode to astro the reason we're going to do that is
2:15
because astro is by default static so this is a great way to compare apples to apples we're going to do it all at build
2:21
time and so we're gonna see these frameworks at their best and be
2:26
able to compare those two okay so let me look a little bit closer at the code that we've got going on here
2:33
so i've got our index page over here and it goes and gets a bunch of pokemon from a local file
2:38
it then uses static props that's why we're going to have a static page and it takes that set of pokemon and it
2:45
passes it through as props that comes over here into home that then gets sent on to the pokemon list as a prop
2:54
and then over here in our pokemon list we do all of this crazy logic to figure out like how
3:02
all the pokemon stack up and all that sort of stuff and what this code over here amounts to
3:09
isn't really anything practical it amounts to a lot of load
3:15
right so it's just a very concise way of simulating
3:20
having an app that has a complex ui library complex ui components that may
3:25
do a lot of work like graphs or whatever have complex business logic or stores so
3:32
folks might say to me okay but if i were to go and just take all of this code here and then pop it over here into the
3:40
server yes this particular app would be faster and that's absolutely true
3:46
but when you have an application that has complex business logic and it's scattered all over the place it's really
3:53
hard to just make one change that's going to go make the app that much faster so
3:59
i think this actually represents a pretty good test you may not believe me but you know we'll see okay so all right
4:05
let us go and build out an astro app that does this so i'm going to go and bring up another
4:11
terminal and in here i'm going to use this mpm init command now this mkm init command
4:17
is going to use the astro init we're going to give it the template specification for react astro is super
4:23
cool you can do react components you can do view components you can do preact components and you can do them all on
4:29
the same page which is awesome and we are going to call our app pokemon
4:34
astro static right so is pokemon next static we're gonna have pokemon astrostatic so let's go build that
4:40
out do you want me to even do the dependencies yes i do i do not want you to make a get humbly
4:47
proud out of that i do want to be relaxed about my typescript that's not the point of all
4:52
this and let's go see what we've got so i'm going to go into the pokemon astro
4:58
static directory i'm going to do yarn dev and we'll see we've got
5:04
copy that oops and then over here i'm going to stop my current server because it's on port 3000
5:10
and i'll do yarn dev over on the astro side i'll copy that
5:16
and bring up a new tab pop that in there and there we go okay so we've got an astro app placeholder
5:24
stuff so let's go over into our pokemon astro static and see what this is we've got
5:30
components we've got that counter component here basically just a simple counter with plus and minus
5:36
along with the css and then it's got the page which is a dot astro file so
5:42
dot astro is a templating language very similar to jsx
5:48
and what it allows you to do is just do things like for example bring in react components and you just invoke them like
5:54
your egos you get the counter it's got and we're saying that it actually is visible on the client which means that
6:00
the code is going to run over there but it feels a lot similar to jsx
6:06
okay so i'm going to go and take some code from our original next and i'll just bring it in almost
6:11
100 unadulterated so i'll bring in the types first that's going to have our pokemon type
6:17
i'll bring in the pokemon list component and i'm just going to change the
6:23
location of types that's all i'm going to do and then i'm going to bring pokemon json in
6:30
also put it in components you know whatever it's fine it's got to go somewhere and let's see i want to delete
6:35
the counter stuff don't need that and i'll go over to this astro
6:40
and i will remove this import stuff in between these dashes is any javascript you want to run
6:49
and see i'll remove all this header stuff don't need that
6:55
and i'll remove that and now i'm just going to bring in that pokemon so i'll do import pokemon this is the list of
7:01
pokemon from the components directory and that pokemon.json so now i've got my pokemon it's that
7:07
easy and then i'm going to bring in our pokemon list from the components directory
7:13
and then i'm just going to wire that up so let's put that in there dooch and pokemon and save and there we go let's try it
7:21
out let's see okay
7:28
how fast is that that's awesome okay so let us go now and compare these to kind
7:35
of build for build so again astro is going to build static files and next is going to build static
7:42
files if you don't know about static file static files are the fastest way to render a page it basically means that
7:47
you're pre-rendering the page you're building all the html and then you're gonna store it off on something like s3
7:53
and then accessing that is is basically as easy as just making a request s3 and a bang
8:00
there you go so it's really really fast and it's going to be next just as fast as it's going to be asteroid is fastest
8:05
we're going to pair the two okay so on our astro side we're going to do yarn
8:11
build and then we're going to do yarn preview
8:17
all right so that's what that looks like on localhost 3000 and now we're going to do the same thing over on pokemon next static so we're
8:24
going to do yarn build over here and this is going to build a static
8:30
version of that home page and then we're going to do port equals 3001 we want to run them at the
8:38
same time and then do yarn and then start and then that's going to run that built version of the code as
8:45
opposed to yarn dev which would run it in devop all right let's go over here to 3001.
8:52
okay so now let's get some numbers i'm going to open up the inspector i'm going to go over here to the network panel
8:58
and i'm going to hit refresh bunch of times and we're going to look down here so we're getting a load time around say
9:05
40 milliseconds 40 50 milliseconds on average okay so let's go over into our local
9:12
host for astro again we'll do the network no throttling
9:18
again and we'll hit refresh and watch to see how we're doing over here load time is in the seven to eight
9:25
millisecond range astro is a four times improvement over next js in this example
9:32
right out of the box how cool is that all right so why is this actually
9:38
happening well i've filtered it down to just js here and there's no js coming
9:44
out of astro right there's nothing that's running on a client so if i go for example in a view page
9:51
source here you can see that the page source is literally just the html that's it
9:57
we've literally just rendered a static page now if i look over here at the next js side there is a ton of
10:05
javascript coming down even in this built mode even in on a static page
10:10
right and we look at the view page source what we can see is yes
10:16
we're getting all of that html at the top here but we're also getting the entirety of
10:22
that pokemon.json file that we sent to that component
10:28
what does this do it sucks in air it's definitely sucking why are we doing this
10:34
well we're doing this because of the way that next js and and frankly react work
10:41
kind of by default nowadays and that's that there's a rehydration cycle of the
10:46
app on the client so what happens is on the client you get all the app source code and then
10:53
you need to re-run the app to create the running state that you had on the server
10:58
you have to recreate it on the client and so you need all of the data that you
11:04
had on the server so that's why there's that big ball of data in the html
11:10
that's then passed on to the app as its pre-initialized state and then you re-run that whole component
11:18
so in our example that means that that huge use memo calculation
11:25
that we did over in the pokemon list this big boy down here
11:31
is getting run both on the server at build time which is great so we did that yarn build
11:37
that's when this is getting run on our build system right and then we store off
11:43
that html but it also has that big payload of data in it and then on the client
11:50
it's actually getting run live on the client so that means that the
11:55
performance of your site is highly dependent on the performance of the specific
12:01
device that your site is running on and that could be somebody's cheap commodity cell phone in fact actually let's try
12:08
that out let's go over to chrome again and we'll bring up the performance
12:13
insights page this is kind of new this is cool and we're over on 3001 so this is an xjs
12:18
and we'll do a little throttling we'll say that our network is bad we're on slow 3g and we'll say that our
12:24
we got a bad phone so like four times a slowdown now this is a intel mac
12:30
2019 it's a pretty decent machine so we're going to slow it down and we're going to see how that looks okay so
12:36
let's do the measure the page load this is a honestly awesome tool it just came out in chrome just recently i'm loving on
12:42
this okay and these times aren't great we're talking about time to interactive of
12:48
6.69 seconds it's crazy all right let's try
12:54
it over here and then do the same sort of thing we want performance insights pick exactly the same options slow 3g and
13:02
a cpu throttling of four times measure the page load of our astro page
13:09
and we are in the green a 2.12 second
13:14
page load time which is hella better than a
13:21
6.69 page load time in fact again that's a three times improvement for the astro
13:28
page over the next js page and and this is for reals right this is
13:33
actually something that you might actually do i mean obviously not this example in particular but i
13:40
mean this is a for real speed differential so when it comes to this claim
13:46
of less javascript on the page that can make a dramatic dramatic difference in
13:52
the performance of your site it may say to me oh come on jack this is not a fair comparison because i mean
13:58
every site is going to have some interactive elements to it so if i were to bring in an interactive
14:06
element into this astro page it would be just as bad just as bad as the next js
14:11
stuff okay let's try that let's actually do that so i'm going to go over here to our
14:17
visual studio code and we'll go and add a little bit of interactivity here it's not going to be much but we're going to do this
14:24
so over in the astrostatic i'm going to create a new file called login.tsx and it's going to have a login function so
14:32
export a default function called login that returns a login button
14:42
and that login button is going to have an on click which is going to say alert
14:48
log in right ridiculous and we're going to bring that on to our
14:54
page so bring in an index estro and then we'll import it
15:00
and then i'll include it and let's try this out so first i'm going to go into dev mode so am i
15:07
running on master yeah there you go okay i'll run it in dev mode and we'll make sure that it works
15:12
and now we can see our login button but when i click on it nothing happens and the reason is that
15:19
again by default astro thinks that whatever that component is has no
15:25
client-side javascript that's associated with it but it does right so if i already go for example in page source we
15:32
would see that it is just that one button and that's it so the way that we tell it to actually
15:37
do something on the client is you say cool client uh visible so this is going to
15:42
load that login code when that actual element is visible on the screen hit save
15:50
and now i hit log in and it works cool so what's really happening here is
15:55
that i am now in control of the javascript that goes out to the page i
16:00
get to decide which components are client-side interactive
16:05
it is the fundamental essence of the island's architecture we have an sea of static content here but we have
16:13
little islands of interactivity in this case that is our login
16:18
okay let us go and take our login and put it over in our next.js so i'll do
16:26
source over here components and add login and then add that to our index page
16:36
login okay now i've got to go build each one of these i got some pushback on my
16:41
recent video about how i compared dev to dev well let's compare build the build okay so
16:47
let's build out the astro version first and then we'll do that preview
16:54
and now we'll do the same thing over on the next side i'll you know first i'll go make sure it works up for 3001 yarn
17:01
dev and i'll hit login yep works just fine cool
17:07
okay so now let's do our static build
17:12
and again we'll use port 3001 yarn start
17:20
and i'll hit refresh okay perfect looks good now let's get those numbers okay so i'm
17:26
going to go back over here to the network i'm going to make sure that our throttling is off and i'm going to hit refresh a bunch of
17:31
times and still seeing numbers in about the mid 40s
17:36
no appreciable difference right there's we've added the tiniest little
17:42
component we wouldn't go and see any difference from that on the next side again what we're seeing on the next side
17:47
in terms of the performance impact is really just the nexus of having a lot of
17:52
react code go down to the page the react library itself and then all of that
17:58
computation that i'm doing now on the client side with that used memo and all that okay
18:04
now let's go and do the same thing over on our astro sign
18:09
so no throttling again and i'll hit refresh again
18:15
down at the 8 10 millisecond range so even with this 135 k of react library
18:22
what's happening is that the react library is getting parsed but all we're doing is rendering this one
18:29
little button so in terms of the overhead for the hydration and everything else
18:34
it's absolutely minimal so that's why we're seeing almost no performance impact from adding
18:41
this additional code to the page super cool well i hope i've intrigued you about
18:47
astro and you want to try it out for yourself so what we're going to do next is we are going to do a more practical
18:53
example and convert a next.js app that has a bunch of the features that you would expect to test when it comes to
19:00
next js and we're going to convert each one of those to astro and see how we go but before we do that i would like to
19:06
ask you to click on the like button if you like this video and click on the subscribe button if you're really digging on this video
19:12
and thank you so much for all the subscribes that we've gotten recently we're up to almost 70k subscribers it's
19:18
nuts i'm loving this thank you so much okay let's go back into our code
19:24
and take a look at our project so i'm going to close up all these we're done with this part of the
19:30
show and we're going to move on to our
19:37
pokemon next directory in our pokemon next example so pokemon next
19:43
and here we're gonna do yarndev and we'll take a look at 3000 this time
19:49
so this is our pokemon next server we're getting an error because we don't
19:54
have access to this localhost 8080 server that has pokemon json on it so where's that
20:00
so that's over in the pokemon directory there is a bunch of static data that we're going to use kind of as an analog
20:07
for microservice right so i'll go and create another terminal here and i'll go into that pokemon directory
20:15
and i'll do port equals 8080 mpx serve and that's just going to serve out the
20:20
contents of that directory i'll go back over to our 3000 hit refresh and tada microservices alive therefore app
20:28
is alive awesome so what we're looking at here is a nice little app it's got you know
20:33
these these cute little pokemon cards here it's got a header and a layout
20:38
you can type in things like sour and get just the pokemon that have sour in the name you
20:45
can click on a pokemon and get all the information about that that's on its own route so it's a detail route
20:51
and then there's one more thing you can do is you can go api search and search
20:56
for a given keyword like sour and you get back json
21:01
and that powers the search page which is fully dynamic so you can type
21:06
in something like sour and you get all of the sours and all that so pretty cool and what it basically
21:13
demonstrates is the kind of things that you would want to do with next js so
21:19
it's got layouts it's got the ability to have detail pages it's got an api it has
21:26
a page that uses that api so we're trying to stress test everything and make sure
21:32
that we can do all of the stuff we could in xjs with astro let's find out
21:38
okay oh also before i get into i should note that this is all on tailwind so we're going to need tailwind first as
21:43
well okay so let's go and build our astro
21:49
site so we'll go back up a level and we'll do mpm
21:55
and yeah okay so we're just gonna do the same thing we're gonna call this just astro right so pokemon astro we have pokemon next now we're gonna have
22:01
pokemon astro do we wanna install npm dependencies i say yes do i make it a git repo no
22:08
and i wanna be i wanna be relaxed about my typescript man i wanna be relaxed
22:14
okay so we're gonna go into our pokemon astro
22:19
and you would expect when we do yarn dev to get that exact same thing that we did before
22:24
let's do it nope not found on that of course because we're in the detail page cool hello react rocking okay
22:32
so let's get something out of the way already let's get a tailwind in there obviously that's going to be a huge
22:38
piece of thing to set up so i'm going to do mpx astro add tailwind
22:45
so it's going to ask me some things do i want to make a change to my configuration file for astro to go and
22:51
add tailwind and then bring it in as an integration i do do i want to bring in
22:58
the development track do i want to bring in the development dependency i i think i should
23:04
yes all right and do i want to make a minimal tailwind config file yes i do okay so there we go that's it that is
23:11
all i need to do and if i were to go and do yarn dev again i think probably change from like whatever that was to
23:17
like a yeah okay so we've gone to like an aerial that's about as much as you're
23:23
going to see from that okay so that's one of the things that's really cool here right so we got this astro integration stuff that
23:30
makes it really easy to bring in things like tailwind and there's a bunch of different plugins
23:36
there's a whole kind of ecosystem around this okay so one of the first things i want to do is bring in the
23:43
little pokemon card right we want to replicate the pokemon cards
23:48
so i'm going to go over to that pokemon next and bring in the components for the pokemon card
23:54
and go over here to components and paste that in there and i'm going to get rid of the counter because we don't need that
23:59
and then we go to pages and we're going to get rid of that counter stuff up there
24:05
and we really don't need any of that we're gonna change that to a layout
24:11
and let's see so that's okay cool so how do we go and get some data well we
24:17
go and use fetch right so we're gonna have res and we're gonna await the fetch
24:23
from that local host 8080
24:29
pokemon.json that's going to give us back a
24:34
response and then we'll get the illicit pokemon all right so from there let's just do
24:40
for the moment just json.stringify and give it our pokemon
24:49
and there you go i had to reboot the server but yeah little things like that okay so we're making that fetch and we are
24:56
bringing that pokemon in and i gotta tell you you know in comparison to say the
25:02
next js version of this let's go take a look at that so index yeah
25:08
okay so we have get server-side props you know i
25:13
it's a little clunkier right so you got the astro file over here this is what we want to run the top
25:19
and then there you go okay so let's go and bring in our pokemon card
25:25
from that pokemon card i'm going gonna put the import at the top there jack be nice be nice
25:31
and i will use pokemon
25:38
and then i will yeah sure i will go and do that pokemon card
25:44
with the pokemon cool and i'm just going to slice that down to the top 10.
25:51
and in fact i had a bit of a different layout here so i had to like a div in there it's got some columns yeah take
25:56
that in there cool and finish up that div
26:03
and it's class instead of class name let's give it a go
26:08
whoa that was fast cool all right so now let's go and wrap that in an anchor tag
26:18
yeah perfect okay thank you github and uh wrap that up
26:27
a little messy but okay and now if i click on that we get a not found that's fine because we haven't
26:33
actually implemented on that yet all right looking pretty good but we don't have a layout though we don't have a header
26:38
so the way that i'm going to do that i'm not actually going to bring i've got a layout component over here but what i
26:44
want to do is show you how to use astro for something like this so i'm going to go and just copy
26:49
the and then i'm going to use an astro file so instead of a
26:55
tsx file i'm going to use an astro file so i'll say layout.astro
27:01
and paste that in there we're going to change that class name to class and
27:06
change our next link to href
27:11
and then in here instead of children we're going to say slot and that's how you do
27:17
children in the astro context and this is the default slot so if you have the layout
27:25
wrapping some children it goes into slot but you can also do named slots which is super cool
27:32
okay so i'm going to go over here and the last thing i need to do is do this name thing so that's going to come in as an astro prop so i'm going to do astro
27:40
props and then say name and so if we have a name coming in then
27:46
use that so now let's go over here into our index and i'm going to bring in our layout so
27:52
layout from components layout dot astro i have to add that extension
28:00
that's a little weird you know one would think i mean if you're in astro right you
28:05
that should be your fault but whatever okay so name equals jack we'll just drop that in there just to make sure that name thing works
28:12
and then we'll do yeah and make that a little prettier hit save
28:18
okay looks pretty good i got my name in there and if i take that name out it
28:25
goes away let's see yeah nice awesome okay cool so let us continue on let's go and go
28:32
into this detail page and see how that works so now it's about routing right we want to figure out how routing works in our
28:38
new astro framework so let's go into our pages directory and create a new folder called pokemon and
28:45
within that a new file called bracket id dot astro
28:52
very similar to how you might do it in next and what this is is a parameterized route and the parameter in this case is
28:58
the id so we're going to bring in that layout like we had before
29:04
and we'll just wrap our thing in a layout
29:09
all right so interesting issue here so remember how i said that astro is by default static
29:15
so it works kind of the same way that next does when it comes to parameterized routes for static
29:22
what that means is you have to specify this get static paths function
29:28
in your component so we're going to export an async function called git static paths
29:34
and it's going to list all of the paths to the astro that we're going to support
29:39
so to get that we need to have the list of all the pokemon so let's go get that put that in there
29:45
and then for each pokemon you need to return an object we're gonna take that pokemon
29:52
object and we are on return object and that's going to say that we have the params
29:58
which is going to be the id with the pokemon id but we need to
30:03
convert it to a string exactly like we need to do in xjs and then we have the
30:09
props and that's just going to be that pokemon so let's hit save
30:16
and see how we do so yeah okay cool so now it knows all of the routes we're just not actually doing
30:22
anything with that pokemon data so the first thing we're gonna do is get that pokemon data from the astro props so
30:28
pokemon equals astro.props.pokemon
30:35
and then we're gonna json stringify it because that's my favorite thing to do when you don't know what's going on
30:41
hit save and there you go nice all right so we've got all our data cool now we just need to format it so let's go back over into
30:48
our next.js app go into the same exact route and we'll just go and grab all this
30:54
stuff and see how it goes so here we go grab all that and pop that in there
31:01
and uh clean it up a little bit so i got all those class names
31:07
class save and uh let's open style okay we're gonna need to tweak that a little bit so that
31:14
becomes style grid template columns
31:21
1fr 1fr okay
31:26
yeah it looks pretty good holy moly well it's bigger but you know it's fine so okay i'm digging on this
31:34
this is this is good i mean it's got the right stuff you're not having exactly the right layout but it's fine okay
31:40
i love it uh now the next thing we had in here was we had a search field so
31:47
let's go and implement on that search field so go back over here to our
31:52
regular index page on next.js and we'll bring in this form
31:58
i'll go over here to the index page in our astro app and we'll paste that in there
32:05
i'll put that at the top cool and we're not going to use any of the
32:10
unchanged stuff i'm not going to use that class name
32:15
and we'll just leave that value currently at empty
32:21
and we'll see how we go okay cool oh nice we have a uh a field now okay so if i hit sour
32:27
we can see is we've got this q equals sour up there so that's automatic what that's done is the form
32:33
tag has resubmit to the page and now all you need to do is get that
32:39
queue and then filter this list of pokemon by that queue and we're good to go
32:45
so the way that we get that queue is we do this astro.url.searchparams.get
32:52
and get that q and now we're going to filter that pokemon by that q
32:57
and we'll get our filtered pokemon so that would just slice that off to be the top ten hit save and we are good
33:03
we're golden it's sour and we're not gold we're not good so
33:09
what's happening here well if i go over here and i say well let's first off see
33:14
if we're getting a good q value there so q equals and then q
33:19
and let's see so if i go over to my console and i hit refresh few times i should see
33:25
q equals sar a few times and i do not and that's the problem so the problem is the static right so we
33:32
automatically build this page as a static piece of html and at the point
33:38
when we build it we don't have search programs right we don't have q equals our this is a role
33:43
for ssr this is a server-side rendered functionality because every time we get a request we may have no queue
33:51
we may have a queue of a different value so we need to do that computation at server side time
33:58
it's certain we can't do this statically we could i mean you could hack it on the client
34:04
let's not do that okay and we really want to show how to make astro do the ssr thing that's really what the point
34:10
of this is so i'm going to go and get rid of that and the way that we make astro do ssr
34:17
is we turn it into server as opposed to static by output and then we add in an adapter
34:24
and an adapter can get you to things like node or dino
34:29
there's a bunch of different adapters so we're going to do the node ones so i'm gonna do mpx astro
34:35
add and then node it's gonna do a similar sort of thing like we did with tailwind so now it says okay do we wanna bring in
34:42
astro js node we have tailwind already that's kind of cool right showing us what it's gonna do and we're going to
34:47
add in the output server so not static now we're going to go ssr and we're going to bring in that adapter
34:53
for note do we want to do that heck yeah i want to do that and i would want to want to bring in that library too okay cool so uh let's
35:01
see let's uh do yarn dev and see how we go so yarn dev
35:08
all right now we're back on 3000 hit save and there we go cool so it's actually
35:14
looking at that sour all right nice you do iv there we go of course it's not actually
35:20
setting that search value there so let's go do that so let's take that q put it in here for the value
35:27
there we go ivy cool all right now of course the detail page does not work and
35:34
the reason for that is because in moving from the static model to the server model we have lost the get static path
35:42
stuff so we no longer do that we're going to render this detail page on the fly
35:47
that is a disadvantage when it comes to astro you can't per route decide that some routes are server side rendered and
35:55
other routes are statically generated so ssr versus ssg
36:00
so in next.js you can do that in astro you cannot so i'm going to go over here and we'll
36:07
tweak this one so that now we no longer do the static paths we instead
36:13
go and get the list of pokemon and that comes back as i guess all
36:20
pokemon and then within that we just want to find the pokemon that we care about so
36:26
i'll bring a quick find piece of code there let's go and find from the params the id for that pokemon
36:33
and there you go hit save and there you go ivysaur nice and the
36:40
layout's good i don't know you tell me comment section down below tell me what
36:45
i did wrong oh and one more thing okay so uh let's see so if i go to here
36:51
i want to have bulbasaur be up there so let's go do that so i'm going to go here and name
36:58
and say pokemon.name cool okay great
37:04
yeah nice all right now the last thing we want to do is implement on that search page so the first thing we need to do is
37:10
implement a search api so how do we do that well it's very very similar to our old friend xjs so i'm going to go
37:17
here and i'm going to create a pages directory called api and within that i
37:22
am going to create a new file called search dot ts
37:28
hip tip you can't use tsx here you can now use js or ts you can't use tsx
37:35
it's a little thing who knows all right now i'm noticing i haven't actually done types here and it's actually still working which is pretty
37:41
cool so i'm gonna go bring in types from that source i'm gonna go and add this to the source
37:48
directory so there you go got that types in there all right so let's go take a look over at our pokemon card uh okay so let's
37:55
just go back up a directory hit types yeah cool all right good uh now let's go
38:00
over here to our search.ts wow it's being really lacks i guess when it comes to ts i don't care import doesn't work
38:07
but it is very very relaxed all right now i'm going to bring in the code for this and i apologize for that
38:13
sometimes i do this copy and paste stuff but basically we need a get function it's going to give us a request we need
38:19
that pokemon type we're going to do our usual fetch of that local endpoint that's going to give us back our list of
38:25
pokemon we're then going to go and do this kind of sorry a little bit nasty thing
38:30
here where we go in and get the the second item off the request and that's
38:36
actually the the actual request i couldn't figure out a better way to do that but here we go
38:42
so from there we get our search params we've got our queue and they will respond with some json okay so let's try
38:49
this out so i'm going to go back over to our app hit api search q equals sour
38:57
hey got it on the first time so i've done this a couple of times sometimes it doesn't work in the first time sometimes
39:02
it does all right we'll go over now and build our search page so this is basically a completely
39:08
dynamic page that's kind of what i want to show here i want to show us having an api and i want to show us having a
39:14
completely dynamic page like for example if i go back over here so this space is basically all ssr when
39:20
it comes over there's only html there's nothing on the page that has any client-side interactivity go over here
39:27
same thing what i want to show is how to do an island of interactivity which would be this search page so i'm going
39:33
to go and create a new route under pages called search.astro
39:41
and again i'm going to bring in that layout all right and do hello
39:49
and do search and now i want to create a completely dynamic search page component so i'm
39:55
gonna go over here to components i'm gonna create a search page dot tsx file
40:01
pop in my react code i apologize again for just doing that copy and paste but you know so this is
40:07
not particularly unique code so we've got you know use state and use effect up at the top here we're bringing in our
40:12
pokemon type bringing our definition pokemon card all right so cool you can use that pokemon card in astro context
40:19
you can use it in react context all good then we're gonna go and have our query
40:24
that's going to hold the data basically from this input we're going to have the pokemon that gets returned from the service whenever
40:31
we change that query we're going to run that use effect which basically does the api search that we just created
40:38
gets json back and sets that list of pokemon pretty simple
40:43
all right let's hit save and then we gotta go use this we'll go over into search.astro we'll bring in
40:51
our search page from the components
41:01
and then we'll instantiate it all right let's see search
41:08
sour and it doesn't work well so why does it work well it doesn't work because again you need to put in that client
41:14
stuff so client let's just say for example client onload so when the page loads load up this component whether
41:21
it's visible or not and there we go and type in essay you are and there you go
41:27
it's really important to know that this client stuff is only available
41:33
in dot astro so when you think about porting over your next js code right you
41:39
think about how the page lays out and you're going to want to go and lay it out so that you can lay it out in
41:45
astro and then you can specify okay this part of the page is going to be static this part of the page is going to be
41:52
dynamic and client-side and if you need to talk between those
41:57
components if you've got multiple islands of interactivity on the same page
42:02
you can do that through a store right you could use redux for that if you have that already there's a really good store
42:11
that's linked to on the astro site called nano stores it's excellent for doing kind of atomic
42:18
state management and it works across the different frameworks so you can have one nano
42:24
store that is platform agnostic and then that can actually be used by
42:30
view code using at nanostore's view it can be used by pre-act code using atonement stores preact it's really cool
42:36
we can obviously be used by react and it's just a really nice lightweight library that gives the ability to share a state between these different
42:43
frameworks all right well i hope this gets you as excited about astro as i am and about the potential of reusing your
42:50
react code but also giving you the ability to specify what parts of the
42:56
page are dynamic and which parts of the page are static and then
43:01
manage the performance of your site through that mechanism of course if you have any questions or comments i will do
43:08
my best to answer them in the comments section down below if you like the video hit that like button and if you really
43:13
like the video hit the subscribe button and i will see you the next time on the blue collar coder
43:26
you
