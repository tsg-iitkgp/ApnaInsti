# KGPApp

An android app for managing events and other activities of the Indian Institute of Technology, Kharagpur

## Motivation

IIT Bombay and a lot of other sister institutes have an app to ease student's day to day life and easily provide all information to them. [Here are](https://github.com/topics/instiapp) all the repositories associated with IIT Bombay's InstiApp. Since the project is opensource, we will be taking parts of the code from there because,

> Why reinvent the wheel?

## Feature List

[Here is the feature list](https://docs.google.com/document/d/1L4wzuw88JrLyBt1DvnjavtAwhJkXgNSIxJG3yBsLwQ0/edit?usp=sharing) of InstiApp of IITB from which ApnaInsti is derived. Below listed are various features of our IIT KGP's application.

### Body

An Entity inside the campus such as fest groups, all socities, all departments etc can register as a body on the app. Being a body allows them to add details about themselves, relevant links, gain followers, create posts about events and engage the KGP community with them.

Body can have PoR holders managing the operations on the app as mentioned in the roles section.

NOTE: In future, we will allow posting stories by the Body.

A body can be followed by users and these users will get notified when a new event is posted by the Body. In an appropriate fashion, the followed bodies will be shown at top for user.

### Roles

Any user can fall into any of the following three categories and accordingly his responsibilities will be there.

#### Basic User

All the users created on the app fall into this category, and all users retain all the rights given to a Basic User even when they have ascended the user privilege level.

A basic user login will be required for all personalized features such as feed, following bodies etc. A user's device information will be stored in order to provide him with notifications for the events and bodies he was interested in.

At the time of registering, an user is required to fill his name, roll number, branch and profile photo (optional). We plan to introduce verification through ERP in future. Currently, for the purpose of verification, an user is required to upload a photo of his ID card.

NOTE: We will also try to provide ability to follow and message other users in future.

#### Body User

A body user is a Basic user who also has one of the following permissions:

- Add an event
- Update an event
- Delete an event
- Update body
- Modify roles -> Make more body users from the existing Basic users

A Body user can have one to all of the above permissions.

This privilege shall be given to POR holders of various socities and bodies such as Department.

#### Institute User

An institute user is a Basic user who also has one of the following permission:

- Add new body
- Delete body
- Modify body-child relations -> e.g. make CodeClub child of CS Dept.
- Edit location -> edit various locations and their descriptions
- Modify institute roles
- Modify roles for any body

An Institute user can have one to all of the above permissions.

This privilege is suited to GymKhana PoR holders who need access to edit institute wide information and manage all the bodies.

### Events

An event can be created by a body with the following information.

- name
- description
- bodies involved
- image
- website
- start_time
- end_time
- all_day
- venues -> selection based on the available locations

Events can be added with tags as well to make it easy for users to search.

An event can also be followed by users which will allow them to get notified of any updates to the event and also receive a notification before the event starts.

An user can also set not going, interested and going to an event.

### Locations

These are the locations across the campus that are available to be embed in an event. An event can be linked to multiple positions but one location can be linked to only one event at a time.

A location is recognized by multiple parameters such as name, latitude, longitude etc.

### Calendar

A calendar is provided to every user populated with the events happening around him and the event he is interested or is going to. Once an user marks event as "not going", it is removed from his calendar.

### Mess Menu

A hostel entity is associated with Mess menu and these are available on day basis.

Mess menu is fetched using a Google Sheet which can be maintained by the hall GSeC.

### News

News is curated via RSS feeds. Each body which wants itself to be featured in news section, required to add an RSS feed URL to their blog or website.

NOTE: There are plans to improve this method, and allow socities to post news items as well as gather news by itself from various sources.

### Grievances And Communication

Users can register complaints as well as provide communication through comments on events and various bodies of the institute.

There will also be a section to provide feedback and suggestions for the application.

## Technical Dependencies

Below table contains all the major dependencies for the project.

| Purpose | Technology | Remark |
| ------- | ---------- | ------ |
| Mess Menus and other data which doesn't required frequenct updates | Google Sheets | Google Sheets is an easy and scalable way to store and manage information. This should be used to store data that needs to be manually updated and only Read operations are required. We will give edit access to hall mess GSecs. |
| Database for high CRUD | SQLite | Django's inbuilt SQLite is used |
| REST API Backend | Django | We will be using REST API at the backend so that later on we can expand to many other platforms |
| Android App | Java | We will be using native android to create the app and it's interfaces which will query the backend |
| API Documentation | Swagger With Django | Swagger with Django will be used to automatically create the rest API and it's documentation. |
| Task Queue and Handling | Celery with RabbitMQ | We will be queuing tasks and scheduling repetitive tasks using Celery with RabbitMQ as the broker. We will be exploring a few more options if required for better simplicity.
| Push notifications | Google Firebase Cloud Messaging | Firebase comes with a free notification manager and we will be using that to send notifications to the users about their respective events |

NOTE: Apart from the above technologies, there will be some miscellaneous dependencies as well which will come forward as we start with the development.

References:
- http://michal.karzynski.pl/blog/2016/06/19/building-beautiful-restful-apis-using-flask-swagger-ui-flask-restplus/
- https://www.linode.com/docs/development/python/task-queue-celery-rabbitmq/
- https://www.fullstackpython.com/task-queues.html
- https://android.jlelse.eu/android-push-notification-using-firebase-and-advanced-rest-client-3858daff2f50

# FAQ

<details><summary>What is ApnaInsti?</summary>
<br/>
<p>
ApnaInsti has been designed (from IITB's app as base) to be the one common platform for all student activities in IIT Kharagpur. The app consists of two versions:

1) The Android App
2) The Website for Windows, iOS, Android etc.

</p>
</details>

<details><summary>What features does ApnaInsti have?</summary>
<br/>
<p>
Some features that are currently available are:

- A comprehensive feed of all the events happening around the institute
- Mess Menus of all hostels
- Unique pages for all bodies, events and users
- Insti news collated from blogs of major bodies
- Institute calendar which will have information of all the events
- Notifications for new events, updates on events, mentions in PT blogs and so on.
- Quick links for CMS, Academic time table and calendar, VPN, etc.
  
</p>
</details>

<details><summary>Who fills in the events and other data?</summary>

<br/>
<p>
Everything is done by POR holders! If you're a manager/convener or equivalent for a club/IB, login to ApnaInsti and let us know so we can grant you permissions on your club. Once a few people are added, they can also add others from the option to edit the body/club.
</p>
</details>

<details><summary>My hostel has no mess menu!</summary>

<br/>
<p>
Ask your mess councillors/secretaries to update it! For those responsible, you just have to update a Google Sheet, which will automatically update data in the app hourly.
</p>
</details>

<details><summary>What happens when I follow events/clubs?</summary>

<br/>
<p>
When you follow an event, you'll get notification when/if the event is updated. Following a body will get events of the body higher priority in your feed and notifications for new events/news.
</p>
</details>

<details><summary>I updated my profile pic but can't see it!</summary>

<br/>
<p>
Logout and login again whenever you update your profile.
</p>
</details>

<details><summary>How to add an event?</summary>

<br/>
<p>
To add an event, click the add event button in the bottom right corner. It is **highly recommended** that you upload an image, since this could have an effect on how high your event is in the feed. Next you need to add a title, description and choose the organizations and venues. Always choose venues from suggestions instead of writing the full name. Doing so will ensure better priority and other features in the future. When you're done, click the Create Event button.
</p>
</details>

<details><summary>How to update an event?</summary>

<br/>
<p>
On an event page, you should see a pencil icon, clicking which should open the update page. Note that updating events sends out notifications to all people interested/going to the event.
</p>
</details>

<details><summary>How to add events with multiple bodies?</summary>

<br/>
<p>
Approach a higher authority with permissions on all bodies to create the event if multiple bodies are conducting an event. For example, if TLS and TFPS are conducting an event together, approach the GymKhana. If CodeClub and CSE Dept are conducting an event together, approach the ApnaInsti team.
</p>
</details>

<details><summary>I don't see a button to add events!</summary>

<br/>
<p>
Make sure you have your PoR registered for the particular body you want to add events for. If you have just received permissions, close the app and open it again or logout/login from settings. If you're using the website, open a new tab and open InstiApp there again.
</p>
</details>

<details><summary>What's News?</summary>

<br>
<p>
News is collected from blogs. If you're managing a society, you can see a pencil icon on the body page to edit your body, where you can change the blog feed URL. Make sure the URL leads to an Atom/RSS feed. Contact the team for more help.
</p>
</details>

<details><summary>How is the order of bodies decided?</summary>

<br>
<p>
The list of bodies are ordered by the number of followers they have. Want to get your ranking up? Ask people to follow your body! You can include a link to your body's/event's page whenever you are publicising. This link can be obtained with the share button.
</p>
</details>

<details><summary>How do I provide feedback?</summary>

<br>
<p>
Please write a mail to tech.tsgiitkgp@gmail.com or get in touch with the current Technology Coordinator, Gymkhana. You can also create an issue at [ApnaInsti](https://github.com/tsg-iitkgp/ApnaInsti) Github.
</p>
</details>
