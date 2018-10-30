select 
t1.customer_id as id,
t1.customer_sk as customer_sk,
t4.ws_item_sk as item_sk,
avg(t2.ss_promo_sk) as promo_sk,
max(t2.ss_ticket_number) as max_num
from
(
  select c_customer_id customer_id
        ,c_customer_sk customer_sk
        ,c_first_name customer_first_name
        ,c_last_name customer_last_name
        ,c_preferred_cust_flag customer_preferred_cust_flag
        ,c_birth_country customer_birth_country
        ,c_login customer_login
        ,c_email_address customer_email_address
        ,d_year dyear
        ,sum(((ss_ext_list_price-ss_ext_wholesale_cost-ss_ext_discount_amt)+ss_ext_sales_price)/2) year_total
        ,'s' sale_type
  from customer
      ,store_sales
      ,date_dim
  where c_customer_sk = ss_customer_sk
    and ss_sold_date_sk = d_date_sk
  group by c_customer_id
          ,c_customer_sk
          ,c_first_name
          ,c_last_name
          ,c_preferred_cust_flag
          ,c_birth_country
          ,c_login
          ,c_email_address
          ,d_year
  union all
  select c_customer_id customer_id
        ,c_customer_sk customer_sk
        ,c_first_name customer_first_name
        ,c_last_name customer_last_name
        ,c_preferred_cust_flag customer_preferred_cust_flag
        ,c_birth_country customer_birth_country
        ,c_login customer_login
        ,c_email_address customer_email_address
        ,d_year dyear
        ,sum((((cs_ext_list_price-cs_ext_wholesale_cost-cs_ext_discount_amt)+cs_ext_sales_price)/2) ) year_total
        ,'c' sale_type
  from customer
      ,catalog_sales
      ,date_dim
  where c_customer_sk = cs_bill_customer_sk
    and cs_sold_date_sk = d_date_sk
  group by c_customer_id
          ,c_customer_sk
          ,c_first_name
          ,c_last_name
          ,c_preferred_cust_flag
          ,c_birth_country
          ,c_login
          ,c_email_address
          ,d_year
 union all
  select c_customer_id customer_id
        ,c_customer_sk customer_sk
        ,c_first_name customer_first_name
        ,c_last_name customer_last_name
        ,c_preferred_cust_flag customer_preferred_cust_flag
        ,c_birth_country customer_birth_country
        ,c_login customer_login
        ,c_email_address customer_email_address
        ,d_year dyear
        ,sum((((ws_ext_list_price-ws_ext_wholesale_cost-ws_ext_discount_amt)+ws_ext_sales_price)/2) ) year_total
        ,'w' sale_type
  from customer
      ,web_sales
      ,date_dim
  where c_customer_sk = ws_bill_customer_sk
    and ws_sold_date_sk = d_date_sk
  group by c_customer_id
          ,c_customer_sk
          ,c_first_name
          ,c_last_name
          ,c_preferred_cust_flag
          ,c_birth_country
          ,c_login
          ,c_email_address
          ,d_year
          )t1
  left join 
  (select * from store_sales) t2
  on t1.customer_sk=t2.ss_customer_sk
  left join
  (select cs_sold_date_sk,cs_sold_time_sk from catalog_sales) t3
  on t2.ss_sold_date_sk=t3.cs_sold_date_sk and t2.ss_sold_time_sk=t3.cs_sold_time_sk
  left join 
  (select ws_sold_date_sk,ws_sold_time_sk,ws_item_sk from web_sales) t4
  on t3.cs_sold_time_sk=t4.ws_sold_time_sk
  group by 
  t1.customer_id,
  t1.customer_sk,
  t4.ws_item_sk
  limit 100
