# Project

A contracting process can relate to several types of project, including:

* An infrastructure project, as [defined in the Open Contracting for Infrastructure Data Standard](https://standard.open-contracting.org/infrastructure/latest/en/projects/#what-is-a-project) (OC4IDS), like the construction of a bridge
* A larger programme of work, which can have many infrastructure projects, like the construction of a highway of which the bridge is a part
* A public-private partnership project, as described by [OCDS for PPPs](https://standard.open-contracting.org/profiles/ppp/latest/en/)

This extension adds a `planning.project` object to describe the infrastructure or public-private partnership (PPP) project to which a contracting process is related. The identifier for the project ought to be disclosed in `planning.project.id`.

The `planning.budget.projectID` field ought not be used to disclose the identifier for an infrastructure or PPP project. This field is used to disclose the identifier for a larger programme of work as it appears in a budget, like a national or state budget. Since the larger programmes of work that appear in budgets might include many individual infrastructure projects, it is necessary to disclose these identifiers separately.

This extension must be used with the [Location](https://extensions.open-contracting.org/en/extensions/location/master/) extension.

## Example

A buyer plans a contracting process for the design of a bridge.

The contracting process is part of an infrastructure project which covers the design, construction and supervision of the bridge. Information about the infrastructure project is disclosed in `planning.project`.

The buyer publishes a separate OC4IDS dataset, describing its infrastructure projects. `planning.project.id` and `planning.project.uri` reference the project's identifier and URI in the OC4IDS dataset. `planning.project.sector` references the project's classification in the [OC4IDS sector codelist](https://standard.open-contracting.org/infrastructure/latest/en/reference/codelists/#projectsector).

The contracting process and infrastructure project are funded through a larger programme of work to upgrade the nation's highways. The name and identifier of the larger programme of work as it appears in the national budget are disclosed in `budget.project` and `budget.projectID`.

*Note: Contracting processes related to public-private partnership projects are modelled in the same way. Information about the PPP project is disclosed in `planning.project`, not `planning.budget.project` or `planning.budget.projectID`.*

```json
{
  "ocid": "ocds-213czf-0000",
  "id": "1",
  "date": "2024-01-01T00:00:00Z",
  "tag": [
    "planning"
  ],
  "planning": {
    "project": {
      "id": "oc4ids-bu3kcz-0000",
      "title": "State Highway 1 Clutha River Bridge",
      "description": "Design, construction and supervision of a new bridge crossing for State Highway 1 over the Clutha River.",
      "totalValue": {
        "amount": 113000000,
        "currency": "NZD"
      },
      "uri": "http://example.com/projects/oc4ids-bu3kcz-0000.json",
      "sector": {
        "id": "transport.road",
        "description": "Road transport, including roads, highways, streets, tunnels and bridges.",
        "scheme": "oc4idsProjectSector"
      },
      "additionalClassifications": [
        {
          "id": "03.04.05",
          "description": "Bridges for road transport.",
          "scheme": "My local scheme"
        }
      ],
      "locations": [
        {
          "description": "Balclutha, Otago",
          "geometry": {
            "type": "Point",
            "coordinates": [
              169.745,
              -46.2359
            ]
          }
        }
      ]
    },
    "budget": {
      "project": "National Highway Upgrade",
      "projectID": "001-001-002"
    }
  },
  "tender": {
    "id": "1",
    "title": "Bridge design"
  }
}
```

## Changelog

### 2024-03-08

* Recommend use of the 'oc4idsProjectSector' classification scheme for project sector.

### 2021-04-15

* Add infrastructure project example.

### 2020-04-24

* Add `minProperties`, `minItems` and/or `minLength` properties.

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
