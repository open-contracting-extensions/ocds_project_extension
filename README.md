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

Users of this extension should follow the below guidance on the usage of fields which are included in the core OCDS schema:

```eval_rst
=============================== =====
Field                           Usage
=============================== =====
``planning/budget``             This section contains basic information about the budget estimated for, or allocated to, this contracting process at the present time. Further documentation and data about how budgets have been allocated to a contracting process should be published outside of OCDS data, according to the best available standards.
``planning/budget/id``          Wherever possible, this identifier should be possible to cross-reference against formal budget documents.
``planning/budget/description`` A short free text description of the budget allocation for this contracting process. This may be used to provide human readable information on the budget category allocated to this contracting process, and/or, information about the nature and source of the allocation (e.g. conditional, confirmed; any official authorizations given to the budget allocation).
``planning/budget/amount``      The total value of budget allocations for this contracting process. The budget breakdown extension can be used to provide data for multiple budget sources, or to split the budget by years or other periods.
``planning/budget/project``     The name of the project that through which this contracting process is funded. Detailed information should be provided in the extended projectDetail section.
``planning/budget/projectID``   An external identifier for the project that this contracting process forms part of. Required for legacy compatibility with OCDS core.
``planning/budget/uri``         A URI pointing directly to records about the related budget for this contracting process. Where possible this URI should return machine and human-readable representations of the data.
=============================== =====
```

## Changelog

### 2018-04-26

* Add removed field descriptions to guidance section of readme

### 2017-12-29

* Remove repeated descriptions for fields in OCDS core from extension schema

### 2017-07-08

* Updated version to maintain conformance with OCDS 1.1, removing the properties in the extension that deleted `planning/budget/project` and `planning/budget/projectID`.

* Removing unnecessary mergeStrategy and pattern property schema elements

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
