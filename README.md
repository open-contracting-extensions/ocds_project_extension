# Project

This extension adds a `project` object to the `planning` object.

In OCDS, project information is nested under the [`planning.budget`](https://standard.open-contracting.org/latest/en/schema/reference/#budget) object. However, in some cases, budget management systems and project management systems are separate, and it might be important to separately specify:

* The amount reserved in the budget for a specific contracting process
* The project the contract relates to, and the total value of that project
* Sector classifications
* Additional classifications
* Project locations, with options for gazetteer or point locations

This is particularly important in cases of Public-Private Partnerships and large infrastructure projects, where users might want to track all the contracting processes related to the large-scale project, and to understand the individual contracts in the context of their contracting process and overall project values.

## Example

```json
{
  "planning": {
    "project": {
      "title": "Example PPP",
      "description": "The Example PPP project will guarantee the installation of a wholesale shared network that allows the provision of telecommunications services by current and future operators.",
      "id": "example_ppp",
      "uri": "http://communications.gov.example/projects/example_ppp",
      "totalValue": {
        "amount": 600000000,
        "currency": "USD"
      },
      "sector": {
        "scheme": "COFOG",
        "description": "Road transportation",
        "id": "04.5.1"
      },
      "locations": [
        {
          "description": "Local Authority Area: Halton Borough Council",
          "gazetteer": {
            "scheme": "GEONAMES",
            "identifiers": [
              "2647601"
            ]
          }
        }
      ]
    }
  }
}
```

## Changelog

### 2020-04-16

* Remove guidance related to the `planning.budget` object. See [#701](https://github.com/open-contracting/standard/issues/701).

### 2018-05-03

* Add additional guidance on the use of OCDS fields in the context of this extension

### 2017-12-29

* Remove the repetition of OCDS fields in this extension

### 2017-07-08

* Add multilingual support for `Project.title` fields
* Remove multilingual support for non-existent `Project.source` and `Project.project` fields
* Restore `Budget.project` and `Budget.projectID` fields
* Remove obsolete `mergeStrategy` properties

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
