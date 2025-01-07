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
  phone: 
  contact_links:
    # - icon: twitter
    #   icon_pack: fab
    #   name: DM Me
    #   link: 'https://twitter.com/scannell_aidan'
    - icon: linkedin
      icon_pack: fab
      name: DM Me
      link: 'https://www.linkedin.com/in/aidan-scannell-82522789'
  #   - icon: video
  #     icon_pack: fas
  #     name: Zoom Me
  #     link: 'https://zoom.com'
  address:
    street: Room 2.34, Informatics Forum
    city: Edinburgh
    region:
    postcode: 'EH8 9AB'
    country: Scotland
    country_code: UK
  coordinates:
    latitude: '55.94486274094089'
    longitude: '-3.1873566404787894'
  # directions:
  # office_hours:
    # - 'Monday 10:00 to 13:00'
    # - 'Wednesday 09:00 to 10:00'
  # appointment_url: 'https://calendly.com'

design:
  columns: '2'
---
