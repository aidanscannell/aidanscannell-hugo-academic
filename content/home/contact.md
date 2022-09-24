---
# An instance of the Contact widget.
widget: contact

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 130

title: Contact
subtitle:

content:
  # Automatically link email and phone or display as text?
  autolink: true

  # Email form provider
  form:
    provider: netlify
    formspree:
      id:
    netlify:
      # Enable CAPTCHA challenge to reduce spam?
      captcha: false

  # Contact details (edit or remove options as required)
  email: scannell.aidan@gmail.com
  phone: +44 7875583912
  address:
    street: Room 3578, Maarintie 8, Espoo
    city: Helsinki
    region: CA
    postcode: '02150'
    country: Finland
    country_code: fi
  coordinates:
    latitude: '360.1874267019191'
    longitude: '24.82024951126642'
  directions: 
  office_hours:
    # - 'Monday 10:00 to 13:00'
    # - 'Wednesday 09:00 to 10:00'
  # appointment_url: 'https://calendly.com'
  # contact_links:
  #   - icon: twitter
  #     icon_pack: fab
  #     name: DM Me
  #     link: 'https://twitter.com/Twitter'
  #   - icon: video
  #     icon_pack: fas
  #     name: Zoom Me
  #     link: 'https://zoom.com'

design:
  columns: '2'
---
