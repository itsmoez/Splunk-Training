# Do WHAT, HOW and WHY for 

What makes up splunk?

1. **Forwarder** is going to forward off your data 
2. **Indexer** is going to index and process your data
3. **Search head** is going to allow you to query and search your enviroment 

Downloading Splunk

1. Head to splunk website download.
2. navigate to productss --> Free trials& Downloads.
3. download the splunk enteprise edition wiht the 60 day free trial.


Adding Data

We need some add-on for the correct source type. so lets find them first

1. Go to apps/browse more apps.
2. Search for Cisco addon. - Splunk add-on for Cisco WSA and "splunk add-on for unix and linux"

To add the data
1. Settings --> add data --> scroll down to and click upload
2. select your data file --> www1 --> access.log --> nect
3. Change source type to access combined --> next
4. Host field value = web1 
5. Create new index --> call it web and save
6. review --> add more data --> upload again
7. do they same for secure.log for ww1
8. Source_type will be linux_secure
9. Host will stil be web1 --> but create a new index called security
10. Do they same for web 2. make sure the host name for www2 is web 2. all access files go into the web index, secure logs go into security index
11. Do the same for www3 -web3
12. Now add the cisco ironport web log --> sourcetype: Cisco wsa squid
13. Host value cisco --> create new index called cisco --> save

Data should be successfully uploaded. 

Go to Search and reporting --> search index=* --> search over ALL TIME --> Verbose mode


## Data pipeline
![Data pipeline image] ("C:\Users\itsmo\OneDrive\Pictures\Screenshots\Screenshot 2026-08-17 003520.png")

## App vs Add-on

**Apps** are somthing you can launch into - Somethig that had a GUI component. An app will change your stations viewpoint and give you a new front end experience for manipulating data. 

Examples of Apps:
- AWS
- Azure
- Corelight

An **Add-on or a TA** (Technology Add-on) is something you can add to your splunk instance for functionality purposes. It runs in the background. Just think of it as one or more components executing its scripts or configurations in the backgrounds to get the job done.

Examples of Add-ons:
- Crowd strike
- Juniper
- Unix and Linux (What we have added)

## The basics of searching

## Knowledge Objects (KOs)

**WHAT** are they?
KOs are tools used for analysis.

If i wanted to build an alert that will tell me when I've done 50 sales on my website in a day, that alert is a KO.

or

If i wanted to create a tag on my events to show in green when a user logs in ti the web server 2, that tag is now a KO.

KOs are searcahble by all users can be reused as *persistent objects* that live in one app pr more dependents on permission. 

KOs are managed by a Knowledge manager

Splunk best practice for naming KOs.

        <Group name>_<type>_<descirption>
Example  SOC_Alert_LoginFailures

## Permissons

Private = 

## Demo of KOs 
**HOW**
Settings → knowledge section → alerts

Search for index = security to find some data for an alert and to pick fields.
Filter on action = failure, host=web1, eventtype=failed_login user=admin src= any ip for demo
Save as alert.
Give title, use conventional naming i.e SOC_Alert_ExcessiveFailedLogins
Descriptions - failed login attempt from russian ip
Permissions - shared in app
Alert type- default values
Trigger conditions - greater than 0 - you want to know if there was 1 attempt from a malicious ip
Throttling- lets say you had 6 alerts fire in a minute but you only want to be alerted once, then you would select this. - set for 1 minute
Trigger action → add action → log event →send email→put an email→save
Fill in box for log event i.e excessive failed login from russian IP
Edit permissions → Everyone can read only admin can write → save

All arets will be in searches, reports, and alerts

Settings → knowledge section → Event types
New Event type → Name → purchases made on webstore
Search string = index=web action=purchase priority=1 → save
Filter on made my me, edit permissions → all apps → everyone can read and admin can write → permissions will be changed to global
Copy search string and run it in search → scroll to event type and you can see your KO

## Fields 

Fields are key value pairs in the form of field name and a field value
Field names are case sensitive when searching, but field values are not.

Another thing to note about the sidebar is that Splunk tells you a little bit about the fields.
An a means that the field values are alphanumeric
and the hashtag, tells us that the values will be numeric.

how you structure your search can make a difference. A search
with a does not equal field expression ( index=web sourcetype=access_combined categoryId != SPORTS ) set will tell Splunk to search for everything that does not contain the field value of sports for that field.
On the right, the not operator (NOT categoryId = SPORTS ) will tell Splunk to search for everything that does not contain the field value of sports **AND** all events where the category ID field doesn't exist.
So you'll have less events for the does not equal and more for the not operator
because the search on the left is a subset of the search on the right.

## Search Process language

image in docs of splunk syntac and colours
 

Some Commands
- Table : make a table based of the variables and arguments you set in your search
- Rename : rename fields that exist in the data or rename fields that youve calculated from built searches
- Fields : The field command allows you to call on fields you want to include or exclude in your results
- Dedup :  stands for a de-duplicate and it will remove duplicated values from the results from the fields you select to de-duplicate.
- Sort : Will sort based on the arguments you set.

When you search this
```
index=web OR index=security | stats sum(bytes) as Total_bytes 

```
You get 82927431, which is unreadbale

```
index=web OR index=security | stats sum(bytes) as Total_bytes | eval Total_bytes =tostring(Total_bytes, *commas*)
```
When you include the eval and the two arguments (your field, and how you want it seperated) 
You get 82,927,431

Preferences 
- search assitance full 
- turn on auto search format (it starts a new line every time you throw a pipe into the search bar)

you can decide on the other things if you'd like

## Demo of building SPLS

```
index=web
| table clientip, action, catergoryId, status
| where ISNOTNULL(action)
| rename action as "ACTION" , clientip as "Shoppers IP"
| fields - status
```
- Here we made a table of selected fields.
- Action had some nulls so we did that to remove it
- rename to rename
- minus status field to remove that field

```
index=web
|table clientip
| dedup clientip
```

- Firstly it was just table clientip which showed all ips
- dedup removed all duplicates, so only showed unique ips

```
index=web
|table clientip
| dedup clientip
| sort clientip
```
- sort arranges the client ip in ascending order, put a minus (- ) infront to make it descending

## Transforming your search

What is a tranforming command?
- it is a search command that orders the results into a data table.

##### Top
- Finds your deault top 10 values for a field and puts it into a table

#### Rare
- Does the opposite of top
- Finds the least common values

#### Stats
- Calculate statistics
- Count, dc, sum, avg, list, values, etc.

## Example trasforming searches

```
index=security "fail*"
| top src
```

- This serach find the top 10 IPs that failed to login

You can do it by clicking the left field bar by first doing index=security "fails*" and then clicking src --> Top values under reports --> gives you top 20 by default this why

```
index=security "fail*"| top limit=20 src
```

-------
```
index=web
| rare limit=1 categoryId
```
- This serach lets us see tthe top most rare value for categoryId - Sports - 793

vs

```
index=web
| top limit=1 categoryId
```
- This search lets us see the most common value for this catergory

----
```
index=web
| stats count by referer_domain, action
```
- This serach shows the referer domains(the websites people went on), the action they tokk i.e addtocart,prucase etc, and counts the amount of actions per domain per action

```
index=web
| stats count by referer_domain, action
| stats sum(count ) by referer_domain
```
- This gives all the actions taken on each domain

----
```
index=security
| stats values(user) as "Login name", count(user) as "Attempts" by src
| fillnull value="no data availiable"
```
- This serach shows
        - values(user) - shows all the users names(values) under a value header as Login name
        - count(user) as "Attempts" counts the amount of attempted logins
        - src - ip address

- Next to attemps theres a little pen sign that lets you format, or colour the data in green, yellow and red. 


## Transaction command

### What is it?

Groups Multiple related Event into transactions based on associated and related identified fields of interest that span in a timeframe.

It can show you the beginning and endpoint for events and conversations

Max span: 
- max span - this can be set to determine the maximum total time between the first and last event. 
- This sets the entire transaction length that you want to look at.

Max pause:
- is the max time between each individual event
- The default is one minute

Startswith & endswith:
- This is where you can set your variables for keywords, windows event Ids, or other searches of interest. 
- For example, you can look for events that start with the Windows ID of login and ends with the Windows ID of log off.

(table for transaction vs stats in screenshots)

```
index=security
| stats values(user) as "Login name", count(user) as "Attempts" by src
| fillnull value="no data availiable"
```

- This search creates a table that shows the the value of the users - meaning all the users, the attempted logins from each user with the src/ip used to log into that user.
- by cliclking the little pen on the right you can set colours for the amounts of count(user)(logins) - red-yellow-green

## Manpulating data

- Eval
The eval command evaluates fields and allows you to manipulate data to create the calculated results you want, it does the matchs you ask, takes functional arguments (if,null,lookup,tostring)

|Where|Search|
|----|----|
|Cant place before first "|" in the Spl|Place it anywhere in the SPL|
|Comparing values, or searching for a matching value|search on a keyword, or matching value|
|Use with functions|search with wildcards|
|*think boolean operators=where|*think expressional searches=search|

examples 
```
index="_internal" 
| eval epoc_time = strptime(_time, "%s")
| eval human_readable_time= strftime(epoc_time, "%m,%d,%y %H:%M")
| table _time, epoc_time, human_readable_time
```
this changes _time to time from event to epoc time in seconds.
epoc time is a way computers track time. It counts the total number of seconds that have passed since midnight january 1 1970

- table ... shows a table of _time and epoc_time and readble time

```
index=web
| eval status_code = case((status == 404),"not found", (status == 400),"bad request response")
| stats count by status, status_code
```

```
index=web   | eval hash=md5(file) 
| table file, hash
| dedup  file
```

------------
##### WHERE examples
```
index="security" 
| table src, user, action
| where src = "64.66.0.20"
```

Shows a table of src(IPs), user and action where src is this specific IP address. Thats how you use where

```
index="security" 
| table src, user, action
| where like (src,  "64.%")
```

You can also use - Where like(src, "64.%") 
which will return all the IPs that start with 64 - think wildcard

#### SEARCH
if you want to filter on a user you need to use SEARCH 
```
index="security" 
| table src, user, action
| where like (src,  "64.%")
| search user = mailman
```

## Fields part 2
#### Field extraction methods

Use:
regex ---->  when your data is Unstructured 

delimiters ---> when data is structured and splunk can easily seperate fields of a common delimiliter like a semi colon or commas etc

Commands ---> work with rex and erex in your spl
 
Field extractions are a way to organise your data to pull information you want to see

Settings --> Fields--> Fields Extraction--> Open Field extractor

## Demo of fields/regex/delimiter

Another way to get to field extractor

search for an index i.e index=cisco
From one of your events, click the drop down menu
Event actions --> extract fields

To extarct through th gui

Click regular expressions --> highlights parts of the events to add/select fields i.e - ip addresses can be highlighted and labelled ip_address

GET can be highlighted and be extracted as 'Method'
urls can be highlighted and extracted as a domain field
-you will see that fields with the names and values you have picked appeared

Preview mode lets you see before extract below.

Set your permissions after --> Read for everyone and write for admin --> app selected too

If you refresh your search, you should be able to see your extracted fields in your fields menu on the left handside of a index=cisco search

##### Reg and erex
\S+\S@.com
regex101.com

index= cisco | rex field=_raw (<field_name>)"<theregexwemake>"
example

index= cisco | rex field=_raw (<email>)"<\S+\S+@.com>"


### LOOKUP
#### WHat is it
A *lookup* is a **file** that contains **static data** in it that you can use to query in your searches. 

(They can have data that gets updated but in most cases you'd want to use a kv store lookup when working with dynamic data.)

The data in a lookup should be data that is not stored in your indexes, otherwise we would just search those indexes.

They can ass useful info just stored somewhere else besides your index. For example, we can use lookups to add infor about our status codes to display the definition of what each code means, or we can set what products is relevant to the random product IDs weve been seeing.

#### Lookup Commands
- Lookup - The lookup command will be used to load those results contained in the lookup. - you can use this command to view what data's in the look up
- OUTPUT - Overwrites existing fields
- OUTPUTNEW - DO NOT Overwrite existing fields
- inputlookup - Use the input lookup command to search the contents of a lookup table
- outputlookup - the output lookup command to write to that lookup table.

To create a lookup:
Go to Settings --> Lookups --> add Lookup file tables, and then just click on New Lookup and set your parameters and you're off to the races.


upload mock.data.csv into look up tbale --> call it people.csv
save --> change the permissons and put it in search.
```
|  inputlookup peopleinfo.csv
```
this shows what in the csv in splunk 

you can filter on specific users by us ing WHERE

|  inputlookup peopleinfo.csv where ("state = New York")

##### LOOKUP definitions

Go to lookups --> lookup definitons --> add new
Name = peopleinfo(same as file), Type = filebased

index=web
| table productId
| dedup productId

shows 16 product ids

you need to then manually add 16 type of products to the product ids under a description field
Upload that file to lookups with same name productinfo.csv --> change the permissions

Index=web action=purchase
| lookup productinfo.csv productId OUTPUT description 
| table productId description 
| where isnotnull(productId)

Index=web action=purchase
| lookup productinfo.csv productId OUTPUT description 
| stats count by productId description
| where isnotnull(productId)
| sort - count

Gives extra values to your fields

#### Visualise your data
-Chart, timechart

Find out the difference between stast, chart and timechart

Timechart - chart is the ability to view statistical data over time.
chart - can make multiple types of charts, stacking available
stats- can easily alter any stats table

Options you can set:
Stacking - stacks the values for each field vertically on the same bar chart. When off, the fields will be displayed horizontally across right next to eachother
Overlay - Add two lines charts over each other
Trellis - Display multiple charts at once
Multi-series - will determine if your fields are sharing a Y-axis or not

## Demo visulaizations

index=web | timechart avg(bytes) by host
- shows a timechart line graph of each web servers bytes by time

index=web
| where isnotnull(action)
| timechart count by action

Chart overlay will show a line through a bar chart

Save as dashboard panel
complete dashboard title and panel title. Cab see it in dashboards sections

index=web
stats coint by action
- good for ports use circle chart

index= web action=purchase
| stata counts 
- shows number of purchases made

you can move your charts around

what is actually being sold
index=web action = purchase
| lookup productinfo.csv productId Output description
| chart count over host by description useother=f limit=0

Number of failed logins by user
indux=securtiy eventtype=failed_login
| timechart count by user useother=f usenull=f limit=5


## Visualisations 2

Additional commands
Iplocation - add location info to your visualisations
geostats - calculate functions to display on a cluster map - uses log and lat
addtotals -  allows you to add all the field values for each column
trendline - overlay a line on a chart that shows a moving average

## More demo 
index= _internal sourcetypE_splunkd
| timechart count
| trendline sma5(count) as "Over moving average of total events"

- the number between sma and () determine how many days are recored


## Reports and drilldowns

reports are saved searches

Make a home dashboard :
Settings -->Dashboards -->Edit--> Set as Home Dashboard

## Demo of generating reports, drill downs, home dashboards
```
index=_internal log_level=*
| Date= strftime(_time, "%m/%d/%Y")
| where isnotnull(reason)
| table log_level, reason, Date
| dedup reason
| sort Date
```

Save as dashboard panel -->

watch vid 30 again and make notes

## Alerts
##### WHAT
An **Alert** based on searches you have set to run on a schedule or in real time to check for specific criteria being checked

With alerts you can create trigger actions which will notify analysts if the alert has been triggered. This can be through logs, send an email, webhook, custom action.

Alerts Demo 
- Instructor was collecting logs on her computer for the last 30 minutes. Thats the data/index she will be looking at the create this alert

Settings -->Add data-->monitior-->Local windows network monitoring

When saving as alert --> select For each result in trigger.
Do trigger actions

## Tag & Events

Tagging your events can add quick reminders for yourself. They serve as a aid for reading data

Event types are something you can create to share knowledge with your peers through highlighting and colour coding your events.

For example, maybe you want all status codes of 200 to display as green and all stastus codes of 404 to display as red. 

They serve as a way to caterogorise your data.

To see where your tags that you have made are:
Settings-->Tags-->List by field value pair-->Owner:you
Change permissions so people can see your tags

## Macros
What is it
Macros are shortcuts for you to use in your searches. They ae saved off searches that can be ran in the search bar just by typing the name of the macro.

So let's say you had a really long query that was the same search you had to run every day. Well, you could make a macro, and just call it by the name in the search bar, and save yourself the time by not having to type out that lengthy, repeatable search every day.

Macros also take arguments with them, and you have to surround the arguments with parentheses, and you can include one or many arguments with your macro.

Ctrl-Shift-E to expand the macros

To create a macro
Settings--> Advanced search--> Search Macros--> Click add new oneWhen you created your macro and what to call it, you have to use back ticks. I.E `Macro_name`

Example of creating a macro
Heres a search that finds the top 5 IPs that are seen in our indexes

Index=web OR index=security
| top src limit=5

We go to Advanced search-->Search Macros-->Add new
Name= top5 
Definition = This is where you put your searches 
Index=web OR index=security
| top src limit=5
Save --> Search Macros

In the search you can search `top5` to get the same search

## Workflow Actions
There are 3 available workflow actions which provide different functionalities

1. Create workflow action
- Using Splunk web, create a new workflow action to eith push, pull or search data

2. Configure Workflow action
- Within the Web GUI, configure the previously determined action type with a 3rd party source

3. Validation 
- Check to see if data is being pushed, pulled or searched for after configuration

Splunk provides 2 main workflow actions
        GET                                POST
 Create HTML links to            Generate HTTP POST request to
  intereact with sites                 specified URI
 
 Ex: Google searches,               Ex: Create entries in 
 querying WHOIS databases          management systems, forums 

With GET, you can leverage a web resource and send one of your fields in Splunk to that web resource to then gain additional information from it. For example, you can create an action for Splunk to look up win event log codes, and then see them displayed right in your events, rather than having to navigate to a website each time and look up what that win event log code means.
Next with POST, this is where you want to be pushing your data. An example would be sending data to input into an online form, a SNOW ticket, or creating tickets based off of events of interest.

Theres also search but its advanced

#### Get wrokflow action

Settings -->Fields-->Workflow actions

Whois.domaintools.com - web resource that can look up ip address

index=web to grab an ip

copy and paste an ip into tool

- Workflow action will be displayed under Events action button when you pull down on the events

Go to workflow actions and ass new
give a name i.e Ip whois lookup
Label = whois:$clientip$
In the url, copy the url but wrap the field in $
so instead of domain.com/ipaddress
it should be domain.com/$clientip$

Change the permissions

Do index=web again and look for ip address pull down on events and you will see whois:(whateverip the evenet/log has)









