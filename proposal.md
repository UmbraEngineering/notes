
# Resturaunt Application Proposal

The basic idea of this project is that it will be a web application from which resuraunt owners/staff can keep track of and communicate efficiently the state of their business. In the most common use case, this will be run on several machines, on site, in different key places (at the door to seat people, with servers to take orders, in the kitchen to recieve orders, etc). For the time being, this application will _not_ be used for payment. We may add some sort of ability to record payments recieved, but it won't actually process them (I don't want to deal with POS systems or card processing).

Yes, this is a very ambitious project idea. Yes, it will take a while to finish. Yes, it will be difficult to build and probably more difficult to market successfully. But it is still a fairly new niche (not really new, but new enough) and I don't think anyone has done it well enough yet that the market is cornered just yet. If we can get in on this market, it could extremely profitable.



## Use cases/description of features

- Creating an account also creates a new subdomain, through which the whole application is accessed. (eg. `joesburgers.thewebapp.com`)
- Each account (site) has its own users with their own logins.
- The account owner (manager) can perform administrative tasks on their own site/users.
- The manager can upload a floorplan of their place (and maybe have a simple "floorplan builder" tool) which will be the main view for the site.
- The manager can then add "tables" to the floorplan, which will act as buttons/indicators displayed on the main screen.
 - Tables will have their own sub-screen from which orders can be taken, information can be managed, etc.
 - Tables can have some basic meta-data attached to them (like number of available seats at this table)
 - Tables will also have some basic state information (occupied, number of people at the table, how long they've been there, are they waiting on something?, etc)
 - Tables can be grouped into "sections" for bulk operations and information (eg. how many tables in section A are full?)
 - Tables and/or sections can be assigned to individual users (servers/wait staff)
- Sites will also have a menu defined which will be a customizable, categorized list of items and prices.
 - When a server is taking an order, they will select a "order" button on the table's screen, which will pull up an sub-screen
 - From this screen, they can add items from the menu (and optionally custom items), building up an order list
 - Each item that is added can also have notes added to it, as well as predefined modifiers (eg. "no tomato", or "extra cheese [+50 cents]")
  - That list of modifiers will be a combination of a "global" modifiers list, as well as an optional, per item list
 - When the server is done taking the order, they will push a button to submit the order into the system
- Each site will have a (or multiple: eg. main kitchen, bar, etc) kitchen screen(s), which will be a bump-list of orders that have been submitted by servers
 - Orders on the kitchen screen will have times (when the order came in) and will be listed in that order by default
 - Orders will be rearrangable on the kitchen screen, allowing items to prioritized and organized



## Technologies/methodologies

- Node.js backend
- Mongo for the main data store
- Socket.io for most communication needs
- The whole app will need to be built to be scalable, no one instance of the app can get out of sync with another
- A lot of the app will basically be one big event bus, pushing data around between different screens



## Amendments

- We should support formatting printables (like order slips for a kitchen, or receipts)
- We should support the splitting of tickets (so you can have multiple separate payments for portions of a bill) as well as the ability to add to an existing order in a way that does not complicate already in process tasks. (for example, adding a dessert to someone's order after they have finished eating should proc events like sending the dessert order to the appropriate kitchen, but should not re-proc events like sending the original dinner order to the kitchen. we will need to decide what the appropriate way of handling amendments is while still keeping orders and tickets organized.)







