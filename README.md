# ICalendar

[![Build Status](https://travis-ci.org/lpil/icalendar.svg?branch=master)](https://travis-ci.org/lpil/icalendar)

A small library for generating ICalendar files.

## Usage

```elixir
events = [
  %ICalendar.Event{
    summary: "Film with Amy and Adam",
    dtstart: {{2015, 12, 24}, {8, 30, 00}},
    dtend:   {{2015, 12, 24}, {8, 45, 00}},
    description: "Let's go see Star Wars.",
    location: "123 Fun Street, Toronto ON, Canada"
  },
  %ICalendar.Event{
    summary: "Morning meeting",
    dtstart: {{2015, 12, 24}, {19, 00, 00}},
    dtend:   {{2015, 12, 24}, {22, 30, 00}},
    description: "A big long meeting with lots of details.",
    location: "456 Boring Street, Toronto ON, Canada",
    alarms: [%ICalendar.Alarm{minutes_before: 23}]
  },
]
ics = %ICalendar{ events: events } |> ICalendar.to_ics
File.write!("calendar.ics", ics)

# BEGIN:VCALENDAR
# CALSCALE:GREGORIAN
# VERSION:2.0
# BEGIN:VEVENT
# DESCRIPTION:Let's go see Star Wars.
# DTEND:20151224T084500Z
# DTSTART:20151224T083000Z
# LOCATION: 123 Fun Street\, Toronto ON\, Canada
# SUMMARY:Film with Amy and Adam
# END:VEVENT
# BEGIN:VEVENT
# BEGIN:VALARM
# TRIGGER:-PT23M
# ACTION:DISPLAY
# DESCRIPTION:Reminder
# END:VALARM
# DESCRIPTION:A big long meeting with lots of details.
# DTEND:20151224T223000Z
# DTSTART:20151224T190000Z
# LOCATION:456 Boring Street\, Toronto ON\, Canada
# SUMMARY:Morning meeting
# END:VEVENT
# END:VCALENDAR
```

## Homework

- https://en.wikipedia.org/wiki/ICalendar
- http://www.kanzaki.com/docs/ical/dateTime.html
