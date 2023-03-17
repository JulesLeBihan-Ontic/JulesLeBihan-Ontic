# dim_platform

Field | SCD Type | Description
:--- | :--- | :---
`platform_spec_name` | Type I | `Name of platform data source group`
`platform_name` | Type I | `Ontic platform name (label)`
`source_system_id` | Type I | `Identifies system where source data originates (e.g. global)`
`manufacturer` | Type I | `Name of craft manufacturer name (e.g. Airbus, Boeing)`
`current_family` | Type I | `High level craft classification (e.g. A330/A340 Family, 727 Family)`
`aircraft_type` | Type I | `Aircraft type name (e.g. A340, 727)`
`master_series` | Type I | `High level series name of craft within a type and family (e.g. A340-300, 737-200)`
`aircraft_series` | Type I | `Mid level series group name of craft (e.g. A340-300X, 737-200F)`
`aircraft_sub_series` | Type I | `Lower level sub-series of craft  (e.g. A340-313X, 727-200F (M) Advanced)`
`engine_manufacturer` | Type I | `Name of manufacturing company for engine (e.g. Teledyne Continental Motors,  Rolls-Royce Allison)`
`engine_family` | Type I | `Engine high level family group (e.g. T63 / 250 Family)`
`engine_type` | Type I | `Engine type name`
`engine_master_series` | Type I | `Top level classification for engine series within family group (e.g. 250-C20)`
`engine_series` | Type I | `Engine series name (e.g. 250-C20)`
`engine_sub_series` | Type I | `Lower level of engine series hierarchy (e.g. 250-C20B, 250-C18C)`
`platform_key` | Type 0 | `Generated unique primary key`

## Global

```sql
select distinct
    platform_spec_name      as platform_spec_name
  , ontic_platform_name     as source_system_id
  , manufacturer            as manufacturer
  , current_family          as current_family 
  , type                    as aircraft_type
  , aircraft_series         as aircraft_series
  , master_series           as master_series
  , series                  as aircraft_series
  , aircraft_sub_series     as aircraft_sub_series
  , engine_manufacturer     as engine_manufacturer
  , engine_family           as engine_family
  , engine_type             as engine_type
  , engine_master_series    as engine_master_series
  , engine_series           as engine_series
  , engine_sub_series       as engine_sub_series
  , platform_type           as platform_type            
from platform_ontic_spec_single
where active = '1'
and coalesce(manufacturer, 'XXX') != '#N/A'
and coalesce(manufacturer, engine_manufacturer) is not null
;
```

