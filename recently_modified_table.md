# Recently Modified Tables

```
select tab.owner as table_schema,
       tab.table_name,
       obj.last_ddl_time as last_modify
from all_tables tab
join all_objects obj on tab.owner = obj.owner
     and tab.table_name = obj.object_name
where tab.owner not in ('ANONYMOUS','CTXSYS','DBSNMP','EXFSYS', 'LBACSYS',
     'MDSYS', 'MGMT_VIEW','OLAPSYS','OWBSYS','ORDPLUGINS', 'ORDSYS','OUTLN',
     'SI_INFORMTN_SCHEMA','SYS','SYSMAN','SYSTEM','TSMSYS','WK_TEST',
     'WKSYS','WKPROXY','WMSYS','XDB','APEX_040000','APEX_PUBLIC_USER','DIP',
     'FLOWS_30000','FLOWS_FILES','MDDATA', 'ORACLE_OCM', 'XS$NULL',
     'SPATIAL_CSW_ADMIN_USR', 'SPATIAL_WFS_ADMIN_USR', 'PUBLIC')
      and obj.last_ddl_time > (current_date - INTERVAL '60' DAY)
order by last_modify desc;
```

[BACK](/README.md)
