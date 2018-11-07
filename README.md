SELECT 
   t.pushId  AS  session_id,
   imei,
   t.optType,
   non_stru_field      
FROM bicoredata.dwd_evt_bisdk_customize_dm 
LATERAL VIEW JSON_TUPLE(regexp_replace(non_stru_field,'\\^',','),'optType','pushId')t  AS optType,pushId
WHERE pt_d='20171021' 
   AND pt_service='music' 
   AND oper_id='K098'
   AND t.optType='1'
   LIMIT 50
