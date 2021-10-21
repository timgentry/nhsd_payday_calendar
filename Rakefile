desc 'Generate an ICS calendar of NHS Digital paydays'
file 'nhsd_paydays.ics' do |t|
  require 'icalendar'
  require 'ndr_support/working_days'

  class Integer
    # Returns a date of the number of working days prior to a given date
    def working_days_ago(date)
      times do
        date = date.prev_day
        date = date.prev_day while date.public_holiday? || !date.weekday?
      end
      date
    end
  end

  last_known_public_holiday = Date::HOLIDAYS.last.end_of_month
  
  # Create the calendar
  cal = Icalendar::Calendar.new
  cal.x_wr_calname = 'NHS Digital Paydays'
  cal.x_apple_calendar_color = '#005EB8'
  cal.timezone do |t|
    t.tzid = 'Europe/London'
  end

  # Iterate over the coming months for which we know public holidays and create calendar events
  date = Date.today
  while date <= last_known_public_holiday
    # Calculate payday
    payday =
    if date.month == 12
      # December
      # TODO: Confirm that it is first working day before the 25th
      1.working_days_ago(date.end_of_month - 6.days)
    else
      3.working_days_ago(date.end_of_month + 1.day)
    end

    # Create an all day event and add it to the calendar
    event = Icalendar::Event.new
    event.summary = 'Payday'
    event.ip_class = 'PRIVATE'
    event.dtstart = Icalendar::Values::Date.new(payday)
    event.dtend   = Icalendar::Values::Date.new(payday + 1.day)
    cal.add_event(event)

    date += 1.month
  end
  
  cal.publish
  File.open(t.name, 'w') do |file|
    file.write(cal.to_ical)
  end
end
