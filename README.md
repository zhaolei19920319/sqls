# sqls

# test xingtb
 public static final String s1009 ="select substr(r_reason_desc,1,20) as r_reson\r\n" + 
            "        ,avg(ws_quantity) as lyp1\r\n" + 
            "        ,avg(wr_refunded_cash) as lyp2\r\n" + 
            "        ,avg(wr_fee) as lyp3\r\n" + 
            "  from web_sales, web_returns, web_page, customer_demographics cd1,\r\n" + 
            "       customer_demographics cd2, customer_address, date_dim, reason \r\n" + 
            "  where ws_web_page_sk = wp_web_page_sk\r\n" + 
            "    and ws_item_sk = wr_item_sk\r\n" + 
            "    and ws_order_number = wr_order_number\r\n" + 
            "    and ws_sold_date_sk = d_date_sk and d_year = 2001\r\n" + 
            "    and cd1.cd_demo_sk = wr_refunded_cdemo_sk \r\n" + 
            "    and cd2.cd_demo_sk = wr_returning_cdemo_sk\r\n" + 
            "    and ca_address_sk = wr_refunded_addr_sk\r\n" + 
            "    and r_reason_sk = wr_reason_sk\r\n" + 
            "    and\r\n" + 
            "    (\r\n" + 
            "     (\r\n" + 
            "      cd1.cd_marital_status = 'D'\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_marital_status = cd2.cd_marital_status\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_education_status = 'Primary'\r\n" + 
            "      and \r\n" + 
            "      cd1.cd_education_status = cd2.cd_education_status\r\n" + 
            "      and\r\n" + 
            "      ws_sales_price between 100.00 and 150.00\r\n" + 
            "     )\r\n" + 
            "    or\r\n" + 
            "     (\r\n" + 
            "      cd1.cd_marital_status = 'U'\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_marital_status = cd2.cd_marital_status\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_education_status = 'Unknown' \r\n" + 
            "      and\r\n" + 
            "      cd1.cd_education_status = cd2.cd_education_status\r\n" + 
            "      and\r\n" + 
            "      ws_sales_price between 50.00 and 100.00\r\n" + 
            "     )\r\n" + 
            "    or\r\n" + 
            "     (\r\n" + 
            "      cd1.cd_marital_status = 'M'\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_marital_status = cd2.cd_marital_status\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_education_status = 'Advanced Degree'\r\n" + 
            "      and\r\n" + 
            "      cd1.cd_education_status = cd2.cd_education_status\r\n" + 
            "      and\r\n" + 
            "      ws_sales_price between 150.00 and 200.00\r\n" + 
            "     )\r\n" + 
            "    )\r\n" + 
            "    and\r\n" + 
            "    (\r\n" + 
            "     (\r\n" + 
            "      ca_country = 'United States'\r\n" + 
            "      and\r\n" + 
            "      ca_state in ('SC', 'IN', 'VA')\r\n" + 
            "      and ws_net_profit between 100 and 200  \r\n" + 
            "     )\r\n" + 
            "     or\r\n" + 
            "     (\r\n" + 
            "      ca_country = 'United States'\r\n" + 
            "      and\r\n" + 
            "      ca_state in ('WA', 'KS', 'KY')\r\n" + 
            "      and ws_net_profit between 150 and 300  \r\n" + 
            "     )\r\n" + 
            "     or\r\n" + 
            "     (\r\n" + 
            "      ca_country = 'United States'\r\n" + 
            "      and\r\n" + 
            "      ca_state in ('SD', 'WI', 'NE')\r\n" + 
            "      and ws_net_profit between 50 and 250  \r\n" + 
            "     )\r\n" + 
            "    )\r\n" + 
            " group by r_reason_desc\r\n" + 
            " order by r_reson\r\n" + 
            "         ,lyp1\r\n" + 
            "         ,lyp2\r\n" + 
            "         ,lyp3 limit 100";
