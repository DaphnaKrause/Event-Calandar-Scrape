# Event-Calendar-Web-Scrape
How I scraped my cities event calendar <a href="https://www.visitgainesville.com/events/" title="visitgainesville.com">visitgainesville.com</a>

## The Plan
I wanted to get a searchable list of events that were happening in Gainesville so I wouldn’t miss something important that needed to be reported on in my Newsroom.

Usually, I would have to be clicking through these pages at least every month so it became hard to manage.

### Step 1: 
I inspected the pages HTML finding out where the

- Event_Name was:
h2 class=“tribe-events-list-event-title"

- Date_start was:
<span class="tribe-event-date-start"

- Date_end was:
<span class="tribe-event-date-start"

- Address was:
<span class="tribe-street-address"

- City was:
<span class="tribe-locality"

- and URL Link: a href="https://www.visitgainesville.com/venue/florida-museum-of-natural-history/" title="Florida Museum of Natural History">Florida Museum of Natural History</a>

### Step 2:
I then imported the libraries I needed (I ended up not using time because the server didn’t need a sleep function.)

I then wrote my header after getting an error message saying “Forbidden”

### Step 3:
I wrote a function than a for loop pinpointing the text in the HTML I posted above.

I used `.get_text( )` on everything but the `href`
`.strip( )` was used to take away extra \r\n\t that were being included in the spaces of code I was getting back, I used `.replace(‘\n’,’’)` to change` /n’s` I added to be spaces where I wanted spaces to be.

At the end of this code block, I commented my I took out my function return of `get_event( )` This is because my range in my loop below included this original URL, starting at page=1 through page=10.

See the next step for more information on this range.

### Step 4:
I found out through a lot of trial and error (I even started learning how to use selenium!) that my page could be changed by appending the page number I wished to go to at the end of my URL.

ex.

>for count in range(1, 10):
    >url = ('https://www.visitgainesville.com/events/list/?tribe_event_display=list&tribe_paged=')
    >new_url = (url + str(count))

This allowed for the pages to be read into the for loop that scraped the html above.


### Step 5:

The last thing I did was to write my scrape into a CSV, which I did that through a for loop.

ex.

>for item in calenderList:
    >c.writerow(item)
>newfile.close()

The thing that really helped me was that inspected the HTML on the page beforehand to see which div/span tags I needed to target.
