Modern frontend webdevelopment with Islands Architecture

What is an Islands Architecture?
Lets take an e-commerce application page
<Image>
We have an islands of dynamic content on a page and sea of static content on rest of the page. With tradational web application architecure like NextJS or Vue or Angular we send the javascript for entire page, but with Islands architecure we only send javascript to manage the dynamic sections of the page and we leave the rest on the server. 

So which Javascript frameworks do the islands architecture are Deno's fresh and Astro. But only Astro allows to take existing react components and use them as islands in our application, which is why state of JS 2022 shows Astro as trending framework.
<State of js 2022 image>

so lets put NextJS and Astro head to head with small practicle example and see how the performance improved with Islands Architecture. 

in our exmaple app lets render list of pokemon by grouping them with their type and then apply sorting on that type. And now run both apps in SSG(Static Site Generation) mode

-> Page Load time matrics




 

What is Astro


features
->sample Page rendering speeds
->Script Downloads 
->Hydration vs no hydration
->Slow Network 
->Interactive Elements with Islands Mode
->TTL with non-blocking parallel islands loading

https://medium.com/@mirko.tomhave/astro-client-directives-explained-b0daac284c0






