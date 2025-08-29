---
layout: home
title: "Day of Data"
---
Welcome to the Day of Data site, the evolution of SQL Saturday. We help individuals run free data-related community events for database professionals and those working with data across any platform. We have these events listed:
- <a href="#events">upcoming Day of Data events</a>
- <a href="#reserved">reserved dates for future Day of Data events</a>
- <a href="#other">other non-Day of Data events</a>
- <a href="https://sqlsaturday.com/feed.xml">an RSS feed of all events</a>

If you want to know more about events from an organizer, speaker, sponsor, or attendee standpoint, sign up for our [mailing list](http://eepurl.com/hwVBKn)

## <a name="events"></a>Events

These are the Day of Data events that are currently scheduled. If you would like to organize or schedule an event, please visit our [running a new event](http://sqlsaturday.com/newevent/) page.

<table cellspacing=0 class="table table-hover table-borderless table-sortable mt-3" width="100%">
  <thead>
        <tr>
          <th scope="col"></th>
          <th scope="col">Event Name</th>
          <th scope="col">Date</th>
        </tr>
      </thead>
      <tbody>
  {% assign TodayDate = site.time | date: '%s' %}
  {% assign future = 0 %}
  {% for post in site.posts reversed %}
    {% assign EventDate = post.date | date: '%s' %}
    {% if post.testevent != 1 %}
      {% if EventDate > TodayDate %}
        {% assign future = 1 %}
        <tr>
          <td><img src="{{ post.thumb }}"></td>
          <td><a href="{{ post.url | absolute_url }}">{{ post.title }}</a>
          </td>
          <td>{% if post.postponed == 1 %}
                <b>Postponed</b>
              {% else %}  {{post.date | date_to_long_string }}
              {% endif %}
          </td>
        </tr>
      {% endif %}
   {% endif %}
  {% endfor %}
  {% if future == 0 %}
    <tr>
    <td><img src="/assets/img/logos/Just_icon_Color_small.png"></td>
      <td>No future events scheduled at this time
      </td>
      <td>&nbsp;</td>
    </tr>
  {% endif %}
  </tbody>
</table>

## <a name="reserved"></a>Reserved Dates

The following dates are tentative for these cities, but they have asked to reserve the date.
- May 2025 - Redmond (POSTPONED)
- Mar 21, 2026 - Atlanta - AI & BI
- April 17-18, 2026 - SeaQL 2026 Ouddorp (NL)
- May 2, 2026 - Jacksonville 2026
- Tech Community Day / Day of Data Guatamala 2025 - TBD

Please contact the local organizers for these areas if you have questions or concerns.

You can see completed events on the [Past Events](past) page.

## <a name="other"></a>Other Events

Here are some other events that you might find interesting as a data professional:

<table cellspacing=0 class="table table-hover table-borderless table-sortable mt-3" width="100%">
  <thead>
        <tr>
          <th scope="col"></th>
          <th scope="col">Event Name</th>
          <th scope="col">Date</th>
        </tr>
  </thead>
  <tbody>
        {% for block in site.data.otherevents.events %}
        {% assign thumbnail = block.thumb %}
        <tr>
          <td>
            {% if thumbnail %}
              <img src="{{ block.thumb }}">
            {% else %}
               &nbsp;
            {% endif %}
          </td>
          <th scope="col"><a href="{{ block.url }}">{{ block.title }}</a></th>
          <th scope="col">{{ block.date }}</th>
        </tr>
        {% endfor %}
  </tbody>
