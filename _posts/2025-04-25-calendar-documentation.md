---
layout: post
title: Calendar Documentation
permalink: /docs/calendar
---
# Calendar: Setup Guide
## Slack Bot
Go to the [Slack App Panel](https://api.slack.com/apps), select "From a manifest", and select your chosen workspace. Use this manifest in YAML to generate the bot. Make sure to customize things like the request_url to match your backend's url with the endpoint /slack/events, and optionally things like the name and display name. Create the app, then head to the "install app" section, and install the app to your workspace of choice. Add the bot to your channel of choice, then click "Allow". Then, go to your channel, and add your app to the channel by pinging it using "@botname". It should say "Not in channel", and should be added after you send the ping. Click "Add to Channel" when the popup appears. It should say that @botname was successfully added to this channel, and now your bot is ready to use assuming your backend is functioning properly. For usage, refer to the guide below.
```
display_information:
  name: MessageReader
features:
  bot_user:
    display_name: MessageReader
    always_online: false
oauth_config:
  scopes:
    user:
      - users:read
    bot:
      - app_mentions:read
      - assistant:write
      - channels:history
      - channels:read
      - incoming-webhook
      - reactions:write
      - users:read
      - chat:write
      - chat:write.public
      - im:history
settings:
  event_subscriptions:
    request_url: http://spring.opencodingsociety.com/slack/events
    bot_events:
      - message.channels
  org_deploy_enabled: false
  socket_mode_enabled: false
  token_rotation_enabled: false
```
# Calendar: Usage Guide
## Students:
When loading up the calendar page, you will see a calendar view of the current month, alongside any events that may have been posted onto the calendar.
![Image](https://github.com/user-attachments/assets/e1e17c15-2568-4f41-bbfb-36752e75130d)

Gray events indicate daily plans, and orange events indicate events that are assignments that were automatically pulled from the OCS assignments feature.

The three buttons at the top (CSA, CSP, CSSE) denote the different classes that will be displayed on the calendar. Different classes have different Slacks, and to avoid clutter, choose the class that you are in or wish to see the events of to only show those events. The view you are in also determines where the event will be added if you add an event through the calendar page itself.

## Teachers/Student Planners:
In order to populate the calendar with events, if you are doing so through Slack, use this message template in your Slack's designated channel (assignments, most of the time):
```
[Day of Week (Mon/Tue/Wed/Thu/Fri/Sat/Sun)]: Title
• Description
```

An example of this could be:
```
[Thu]: Live Reviews
• Review project progress with teacher
```

It will appear on the calendar on the day of the week specified of the current week.

To add events directly through the calendar, simply click the date you want to add the event on, and fill out the popup.

![Image](https://github.com/user-attachments/assets/34747f7f-fe83-40d5-8dcd-c5fb984a2d43)

To use other features like date ranges and the WeekOf feature, use the following formats:

```
# date ranges
[Day of Event Start - Day of Event End]: Title
• Description

# example
[Mon - Fri]: Code code code!
• Code Code Coding!
```

```
# weekOf
Week of MM/DD
[Day]: Title
• Description

# example
Week of 06/09
[Fri]: Year-End Review
- Review with Mr. M for full year reflection
```
# Feature Overview & Breakdown

### General Features

-   Slack Integration: 

-   Make a message using message template (provided below) for the schedule of your class in selected channel (in this case preset to announcements)

-   Message auto populated into calendar

-   From Calendar Website:

-   Switch between months (using the month tabs on the top of the calendar)

- Switch between month/week/day view

-   Preset to the current month

- Calendar format:
```
[Day of Week (Mon/Tue/Wed/Thu/Fri/Sat/Sun)]: Title
• Description
```
- Example:
```
[Mon]: Live Reviews
• Review project progress with teacher
```

## Technical Documentation

### Backend Overview

The system is designed to handle operations related to calendar events and Slack messages, such as adding, editing, deleting, and retrieving events and messages. Using Spring Boot's capabilities, RESTful APIs are created to interact with a database to store and manage event and message data.

* * * * *

### Key Components

#### Entities:

-   CalendarEvent: Represents a calendar event with fields such as date, title, description, type, and period.

-   SlackMessage: Represents a Slack message with fields such as timestamp and message content.

#### Repositories:

-   CalendarEventRepository: Extends JpaRepository to provide CRUD operations for CalendarEvent entities.

-   SlackMessageRepository: Extends JpaRepository to provide CRUD operations for SlackMessage entities.

#### Services:

-   CalendarEventService: Contains business logic for managing calendar events, including saving, updating, deleting, and retrieving events.

-   SlackService: Handles business logic for managing Slack messages, including sending and saving messages.

-   MessageService: Handles the logic for saving Slack messages to the database.

#### Controllers:

-   CalendarEventController: Provides RESTful endpoints for managing calendar events.

-   SlackController: Provides RESTful endpoints for managing Slack messages and handling Slack events.

* * * * *

### Flow and User Experience

#### Adding Events:

-   Users add new events by sending a POST request with the event details.

-   Endpoint: /api/calendar/add or /api/calendar/add_event.

-   Controller: CalendarEventController handles the request and calls the CalendarEventService to save the event.

#### Editing Events:

-   Users can edit events by sending a PUT request with the updated event details.

-   Endpoint: /api/calendar/edit/{id}.

-   Controller: CalendarEventController calls the CalendarEventService to update the event.

#### Deleting Events:

-   Users can delete events by sending a DELETE request with the event ID.

-   Endpoint: /api/calendar/delete/{id}.

-   Controller: CalendarEventController handles the request and calls the CalendarEventService to delete the event.

#### Retrieving Events:

-   Users can retrieve events using GET requests.

-   Endpoints: /api/calendar/events, /api/calendar/events/{date}, /api/calendar/events/range.

-   Controller: CalendarEventController handles the requests and fetches the events from the database.

#### Handling Slack Events:

-   The SlackController handles incoming Slack events via the /slack/events endpoint.

-   When a message event is received, it calls the MessageService to save the message to the database and the CalendarEventController to add events based on the Slack message content.

#### Saving Slack Messages:

-   The MessageService saves Slack messages to the database by creating a new SlackMessage entity with the timestamp and message content.

### SQLite Databases

#### Persistent SQLite Storage/Data

The Calendar Event and Slack Message Management system utilizes SQLite as its database for persistent storage. SQLite is ideal for this system as it enables fast retrieval and modification of calendar events and Slack messages, ensuring data integrity even if the backend restarts. The system uses JPA and Hibernate (Spring Boot Application features) to interact with the SQLite Database. It uses persistent storage to maintain data even after AWS terminal (deployment) may be reloaded.

#### Table Structure

##### 1\. Calendar Events Table

The calendar_events table stores data about processed calendar events. Each event is represented as a row, and the table includes columns for various event attributes:

-   id: An auto-incrementing primary key that uniquely identifies each event.

-   date: The date of the event.

-   title: The title of the event.

-   description: A description of the event.

-   type: The type of the event (e.g., "meeting", "appointment").

-   period: The period of the event (e.g., "morning", "afternoon").

##### 2\. Slack Messages Table

The slack_messages table stores data about raw Slack messages. Each message is represented as a row with the following columns:

-   id: An auto-incrementing primary key that uniquely identifies each message.

-   timestamp: The timestamp of when the message was sent.

-   message: The content of the Slack message