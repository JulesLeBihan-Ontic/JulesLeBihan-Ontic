# dim_operator

Field | SCD Type | Description
:--- | :--- | :---
`platform_spec_name` | Type I | `Name of operator data source`
`operator` | Type I | `Name of operator`
`operator_region` | Type I | `Geographical region for operator (operators may be in more than one)`
`operator_country` | Type I | `Operator country (operators may be in more than one)`


## Global

```sql
select distinct
      platform_spec_name  as platform_spec_name
    , operator            as operator
    , operator_region     as operator_region
    , operator_country    as operator_country
from platform_cirium_operators
UNION
select distinct
    platform_spec_name  as platform_spec_name       		  
  , operator            as operator
  , operator_region     as operator_region
  , operator_country    as operator_country
from platform_non_cirium_operators
;
```
