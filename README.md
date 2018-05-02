# Budget and projects extension

In the core OCDS, project information is nested within the `budget` building block. However, in some cases, budget management, and project management systems are separate, and it may be important to separately specify:

* The amount reserved in the budget for a specific contracting process;

* The project the contract relates to, and the total value of that project;

This is particularly important in cases of Public Private Partnership projects, or large infrastructure projects, where users may wish to track all the contracting processes related to a large-scale project, and to understand the individual contracts in the context of their contracting process and overall project values.

This extension introduces a `project` object into the `planning` section.

In the OCDS for PPPs profile, this is further extended with sector and location classifications.

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
      }
    }
  }
}
```

## Documentation

The extension introduces the following fields:

```eval_rst
.. extensiontable::
   :extension: budget_project
   :exclude_definitions:
```

## Guidance

Users of this extension should follow the additional guidance below on the usage of fields which are also part of the core OCDS schema:

```eval_rst
=============================== =====
Field                           Guidance
=============================== =====
``planning/budget``             This section contains basic information about the specific budget estimated for, or allocated to, this contracting process. This field should not be used to report the total value of the budget line which funds this contracting process.
``planning/budget/id``          Wherever possible, this identifier should be possible to cross-reference against formal budget documents.
``planning/budget/description`` This field may also be used to provide information about the nature of the budget allocation, e.g. conditional, confirmed; any official authorizations given to the allocation.
``planning/budget/amount``      In addition to describing multi-source budgets, the budget breakdown extension can also be used to provide data to split the budget by years or other periods.
``planning/budget/project``     Detailed information about the project which funds this contracting process should be provided in the planning/project section.
``planning/budget/projectID``   This field is required for legacy compatibility with OCDS core.
``planning/budget/uri``         Where possible this URI should return machine *and* human-readable representations of budget data.
=============================== =====
```

## Changelog

### 2018-05-03

* Add guidance section based on schema descriptions moved in previous update

### 2017-12-29

* Remove repeated descriptions for fields in OCDS core from extension schema

### 2017-07-08

* Updated version to maintain conformance with OCDS 1.1, removing the properties in the extension that deleted `planning/budget/project` and `planning/budget/projectID`.

* Removing unnecessary mergeStrategy and pattern property schema elements

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
