# Paperless-ngx Home Assistant Addon

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

Paperless is an application that manages your personal documents. With the help of a document scanner, paperless transforms your wieldy physical document binders into a searchable archive and provides many utilities for finding and managing your documents.
### Paperless-ngx

## About

_Paperless is an application that manages your personal documents. With the help of a document scanner (see [Scanner recommendations](https://github.com/paperless-ngx/paperless-ngx/wiki/Scanner-&-Software-Recommendations)), paperless transforms your wieldy physical document binders into a searchable archive and provides many utilities for finding and managing your documents._

![Dashboard screenshot](https://raw.githubusercontent.com/paperless-ngx/paperless-ngx/dev/docs/assets/screenshots/dashboard.png)

Read more in the project's [Readme](https://github.com/paperless-ngx/paperless-ngx)

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Home Assistant add-on.

1. Click the Home Assistant My button below to open the add-on on your Home
   Assistant instance.

   [![Open this add-on in your Home Assistant instance.][addon-badge]][addon]

1. Click the "Install" button to install the add-on.
1. Start the "Paperless-ngx" add-on.
1. Check the logs of the "Paperless-ngx" add-on to see it in action.

## Documentation

The documentation for this addon can be found [here](DOCS.md)

## Integrate into Home Assistant

In Home Assistant Information from paperless can be accessed trought a REST-Sensor:
``` yaml
- platform: rest
  unique_id: 5dade7bc-ddb7-442e-bb17-0d379dbf01fb
  resource: http://44849f5f-paperless-ngx/api/documents/?tags__name__iexact=inbox
  headers:
    Authorization: !secret paperless_auth_header
  value_template: "{{ value_json.count | int }}"
  name: "Paperless Inbox"
  icon: mdi:inbox
``` 

In your secrets file you'll have to specify:

```
paperless_auth_header: Token <django-token>
```

You can generate a token by clicking on `Settings -> Django Adminpanel -> Token` in your paperless instance.

## WARNING! THIS IS AN EDGE VERSION!

This Home Assistant Add-ons repository contains edge builds of add-ons.
Edge builds add-ons are based upon the latest development version.

- They may not work at all.
- They might stop working at any time.
- They could have a negative impact on your system.

This repository was created for:

- Anybody willing to test.
- Anybody interested in trying out upcoming add-ons or add-on features.
- Developers.

If you are more interested in stable releases of our add-ons:

<https://github.com/BenoitAnastay/home-assistant-addons-repository>

[maintenance-shield]: https://img.shields.io/maintenance/yes/2025.svg
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[release-shield]: https://img.shields.io/badge/version-3d4fe62-blue.svg
[release]: https://github.com/BenoitAnastay/paperless-home-assistant-addon/tree/3d4fe62
[addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=ca5234a0_paperless-ngx&repository_url=https%3A%2F%2Fgithub.com%2FBenoitAnastay%2Fhome-assistant-addons-repository
[addon-badge]: https://my.home-assistant.io/badges/supervisor_addon.svg