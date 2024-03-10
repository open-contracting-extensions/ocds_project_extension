# Project

This extension adds a `project` object to the `planning` object to describe the infrastructure or Public-Private Partnership (PPP) project to which the contracting process is related.

The identifier for the infrastructure or PPP project to which a contracting process is related ought to be disclosed using the `planning.project.id` field.

The `planning.budget.projectID` field ought not be used to disclose the identifier for an infrastructure or PPP project. This field is used to disclose the identifier for a project in the national budget to which the contracting process is related. Since projects in the national budget might include many individual infrastructure projects, it is necessary to disclose these identifiers separately.

This extension must be used with the [Location](https://extensions.open-contracting.org/en/extensions/location/master/) extension.

## Example

A buyer plans a contracting process for the design of a bridge.

The contracting process is part of an infrastructure project which covers the design, construction and supervision of the bridge. Information about the infrastructure project is disclosed in `planning.project`.

The buyer publishes a separate [Open Contracting for Infrastructure Data Standard](https://standard.open-contracting.org/infrastructure/) (OC4IDS) dataset, describing its infrastructure projects. `planning.project.id` and `planning.project.uri` reference the project's identifier and URI in the OC4IDS dataset. `sector` reference's the project's classification in the [OC4IDS sector codelist](https://standard.open-contracting.org/infrastructure/latest/en/reference/codelists/#projectsector).

The contracting process (and infrastructure project) are funded through a project in the national budget to upgrade the nation's highways. The name and identifier of the project in the national budget are disclosed in `budget.project` and `budget.projectID`.

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
        "description": "Road transport, including roads, highways, streets, tunnels and bridges",
        "scheme": "oc4idsProjectSector"
      },
      "additionalClassifications": [
        {
          "id": "03.04.05",
          "description": "Transport.roads.bridges",
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
      "project": "National highway upgrade 2024-29",
      "projectID": "001-001-002"
    }
  },
  "tender": {
    "id": "1",
    "title": "Bridge design"
  }
}
```

```{admonition} Public-Private Partnership projects
  Contracting processes related to PPP projects are modelled in the same way: information about the PPP project is disclosed in `planning.project`, not `planning.budget.project` or `planning.budget.projectID`.
```

## Changelog

### 2024-03-08

* Update guidance and examples

### 2021-04-15

* Add infrastructure project example

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
