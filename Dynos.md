## Dynos

Your application's code runs on the Heroku Platform inside of structures that we call dynos. Dynos are not dinosaur-related, although that would really give new meaning to the term [runaway process](http://instantrimshot.com/index.php?sound=rimshot&play=true)! Heroku's dynos are just managed runtime containers with a Linux operating system underneath. These containers run the processes that allow your custom application code to run.

## Runtime Containers??

Don't be intimidated by the terminology! Containerization is just a mechanism for keeping running processes isolated from one another. Think of it like this: Containers keep the strawberry jam from mingling with the mustard in your refrigerator so that your breakfast toast always tastes right. Runtime containers are the same thing, except they keep your code and configuration from touching any others. That way your app always tastes just how it should.

Containers also provide separation between two or more dynos running identical instances of your app, accepting client requests, and serving up responses. Even though one request might be served by Dyno A and another by Dyno B, your users won't know the difference. All they see is your application giving them quick responses. When you scale up your app to run on several dynos (or even dozens or hundreds), you've got extra peace of mind. If something goes wrong with your app code on one dyno, all the others can continue serving your customers.