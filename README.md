sql: select * from (select * from adhoc.lwx592137) t1 left join (select * from adhoctemp.tmp_lwx592137_20181121) t2 on t1.id=t2.tmpid；
标记lwx592137的id和name字段是敏感字段 标记tmp_lwx592137_20181121的tempid和tempname是敏感字段
        
        Map<String, Integer> whiteFunctions = new HashMap<>();
        Map<String, List<String>> tableandSensitiveColumns = new HashMap<>();
        List<String> lists = new ArrayList<>();
        lists.add("tempid");
        lists.add("tempname");
        tableandSensitiveColumns.put("tmp_lwx592137_20181121", lists);
        List<String> lists1 = new ArrayList<>();
        lists1.add("id");
        lists1.add("name");
        tableandSensitiveColumns.put("lwx592137", lists1);
        Business business = new Business();
        business.filterSensitiveFields(TestSqls.s205, tableandSensitiveColumns, whiteFunctions);
        
        Set<TResultColumn> tResultColumns = business.getSensitiveColumns();
        System.out.println(tResultColumns.size());
        Iterator<TResultColumn> it = tResultColumns.iterator();  
        while (it.hasNext()) {  
            TResultColumn str = it.next();  
            String tableAndResultColumn = str.getSourceColumn()
                    .gettNameOrAlias().getName() + "."
                    + str.getSourceColumn().getColName()
                            .getName();
            System.out.println(tableAndResultColumn + "===");
        }  
        
        
        结果只有一张表的字段
