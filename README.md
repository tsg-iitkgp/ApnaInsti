# KGPApp

An android app for managing events and other activities of the Indian Institute of Technology, Kharagpur

## Motivation

IIT Bombay and a lot of other sister institutes have an app to ease student's day to day life and easily provide all information to them. [Here are](https://github.com/topics/instiapp) all the repositories associated with IIT Bombay's InstiApp. Since the project is opensource, we will be taking parts of the code from there because,

> Why reinvent the wheel?

## Feature List [WIP]

[Here is the feature list](https://docs.google.com/document/d/1L4wzuw88JrLyBt1DvnjavtAwhJkXgNSIxJG3yBsLwQ0/edit?usp=sharing) of InstiApp of IITB. Below listed are various features as per various entities associated with the application being developed for IITKGP.

## Processes [WIP]

Below flow-charts and classes depict the various methods of interaction between different entities of the application and how they perform their operations.

## Technical Dependencies

Below table contains all the major dependencies for the project.

| Purpose | Technology | Remark |
| ------- | ---------- | ------ |
| Mess Menus and other data which doesn't required frequenct updates | Google Sheets | Google Sheets is an easy and scalable way to store and manage information. This should be used to store data that needs to be manually updated and only Read operations are required. We will give edit access to hall mess GSecs. |
| Database for high CRUD | MySQL | MySQL is an opensource DBMS which can be used to store data with high level of CRUD |
| REST API Backend | Django / Flask with Flask-RESTPlus | We will be using REST API at the backend so that later on we can expand to many other platforms |
| Android App | Flutter / Java | We will be using either flutter or native android to create the app and it's interfaces which will query the backend |
| API Documentation | Swagger With Django | Swagger with Django or Flask will be used to automatically create the rest API and it's documentation. |
| Task Queue and Handling | Celery with RabbitMQ | We will be queuing tasks and scheduling repetitive tasks using Celery with RabbitMQ as the broker. We will be exploring a few more options if required for better simplicity.
| Push notifications | Google Firebase | Firebase comes with a free notification manager and we will be using that to send notifications to the users about their respective events |

NOTE: Apart from the above technologies, there will be some miscellaneous dependencies as well which will come forward as we start with the development.

References:
- http://michal.karzynski.pl/blog/2016/06/19/building-beautiful-restful-apis-using-flask-swagger-ui-flask-restplus/
- https://www.linode.com/docs/development/python/task-queue-celery-rabbitmq/
- https://www.fullstackpython.com/task-queues.html
- https://android.jlelse.eu/android-push-notification-using-firebase-and-advanced-rest-client-3858daff2f50
