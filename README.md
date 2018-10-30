select
    distinct(t2.belong_area_cn_name)
from
(
select 
    country_name 
from biads.ads_hispace_overseas_stat_dm
where pt_d = '20170801'
)t1
join
(
select 
    belong_area_cn_name,
    country_en_name
from bicoredata.dwd_loc_country_ds
)t2
on t1.country_name=t2.country_en_name
limit 1000
