public static final String test1=  "select\r\n" + 
            " a.cc_name as cc_name,\r\n" + 
            " b.cc_class \r\n" + 
            " from call_center aaa join \r\n" + 
            " center bbb on aaa.cc_rec_start_date=bbb.cc_rec_start_date";
            
            
            
            
            
            
            
            
            
            
   public void columnLineage(String sql) throws ParseException, QuantityException {
        this.initActionRoutes(sql);
        if (null != this.actionRoutes && this.actionRoutes.size() > 0) {
            this.analysisActionRoutes();
            
             List<ColumnLineage> columnLineagescc = this.actionRoutes.get(0).getColumnLineages();
             System.out.println(columnLineagescc.size());
             for (ColumnLineage columnLineage : columnLineagescc)
            {       
                 String tableAlias = columnLineage.getAlias().getName();
                 String tableName = columnLineage.getTableName().getName();
                 String colName = columnLineage.getColumn().getColName().getName();
                 if(tableAlias !=null)
                 {
                     System.out.println(tableAlias +"--->" + tableName + "--->" + colName);
                 }
                 else
                 {
                     System.out.println( tableName + "--->" + colName);
                 }
               
            }
           
        }
        
    }          
            
            
            
            
        
