# How to manage security within salesforce

Protip: The security of salesforce should be extremely private in the beginning. By using **Permission Sets, Hierarchy, Sharing Settings, and Profiles** You are giving more access to users, not taking away access. 




### Control Access To Records
[[ Record-Level Security ]]


### Organization-Wide Defaults
This sounds really complicated, but it isn’t. Organization-Wide Defaults, or OWDs, help to show your data model. Are you private, public, or hybrid? Public means that all data is shared with everyone, and private means we lock all information down initially and then strategically open it up to people who need it.  
A hybrid is somewhere in the middle of these two models. How you configure your OWDs has an effect on the rest of your Security settings.

### [[Profiles]]
Once you start learning about Security, you’ll hear a great deal about profiles. The profile that is assigned to you determines many things, including Object access. Do you have groups of people in a similar job function who have common data access needs? Maybe salespeople need access to opportunities, or service representatives need access to cases. Profiles can help you classify access requirements to different types of users.

### Permission Sets

These are additive permissions on top of your profile. You may have zero permission sets or you may have 10 or more. You may have a salesperson with a sales profile who, unlike other sales representatives, needs to have access to a specific object. Permission sets are like the word “and.” Here, you’d give the salesperson permissions for the Sales profile **_and_** something else.


### Hierarchy Settings
[[ Role Hierarchy ]]:

The role hierarchy gets into the realm of record access. If you are a sales manager, do you want to see the opportunities your salespeople are working on? Of course! Just because a profile gives you access to an object, like Contacts, doesn’t mean that you can access them all. Your company may have 1,000 contacts, but by default, you may only be able to access your own 200.  
The role hierarchy also offers an opportunity to roll up access to records on objects. For example, a sales manager, placed above the hierarchy of her sales representatives, will be able to see all their records as well as her own.

### Record Sharing Rules
[[ Sharing Rules ]]

Sharing rules allow you to share information horizontally. The role hierarchy is all about rolling access up, but what if you want a different configuration? Maybe you have two sales representatives who focus on two different markets — one focuses on New York businesses and the other on San Francisco. Is it possible that a business can have an office in both cities? You bet!  
And if so, wouldn’t it be great for each salesperson to know what other deals are coming down the pipeline that will ultimately impact theirs? Yes! So in this case, you may want to share records of all sales representatives with each other. Since they are on the same level of the role hierarchy, sharing rules can help you in this situation.


# Salesforce Identity
[[ Salesforce Identity ]]


### Futher reading

[[Territory management ]]

[[ Apex sharing]]

[[ GDPR ]]

[[ Audit Trails]]