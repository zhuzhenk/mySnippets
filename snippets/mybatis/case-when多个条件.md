```
select 
case when vehicle_fence.type=0 and vehicle_fence.TriggleStatus=0 then 'inside'
     when vehicle_fence.type=0 and vehicle_fence.TriggleStatus=1 then 'outside' 
     when vehicle_fence.type=1 and vehicle_fence.TriggleStatus=1  then 'in' 
     when vehicle_fence.type=1 and vehicle_fence.TriggleStatus=1  then 'out'
     else 'nostatus' end as'围栏状态'
from t_vehicleandfence vehicle_fence
```



