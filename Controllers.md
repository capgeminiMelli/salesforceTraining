Despite the familiar name, this is an area where your Visualforce expertise doesn’t apply to Aura components. One of the staple features of Visualforce is the Standard Controller. By setting a single attribute for a page, you can bind that page to an sObject type, and get a slew of automatic behavior—reading and writing record data, for example—without writing any code. With the Standard Controller, many non-programmers can create totally custom Visualforce pages. There’s nothing like this for Aura components. Creating a component that works with records _requires_ writing code.

First, remember that Visualforce controllers run on the server side, while Aura component controllers run on the client side. And sometimes on the server side, too. Visualforce controllers are written in Apex, while Aura component controllers are written in JavaScript. And sometimes also in Apex.

Visualforce Controller Architecture

Aura Components Controller Architecture

![Visualforce controller architecture](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_dev_lc_vf_concepts/lex_dev_lc_vf_concepts_code/images/a41efb8d5771343f021c93ffabc3d6fe_architecture-vf-vertical.png)

![Lightning components controller architecture](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_dev_lc_vf_concepts/lex_dev_lc_vf_concepts_code/images/1868f09ce39432c42031cd494bd1f9d8_architecture-lc-vertical.png)

As you can see in the illustration, the two are different architecturally. This difference, the client-side controller, affects the code you write. Your Aura component controller code runs on the client, while the data is stored on the server. In the absence of caching, every time you want new data you make a server request of some sort. That’s code you maybe weren’t writing for your Visualforce controllers. Further, remote requests are written in an asynchronous, callback-based style, which might be very different from your existing controller code.