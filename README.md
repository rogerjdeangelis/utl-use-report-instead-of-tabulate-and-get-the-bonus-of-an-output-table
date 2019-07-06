# utl-use-report-instead-of-tabulate-and-get-the-bonus-of-an-output-table
Use report instead of tabulate and get the bonus of an output table 
    Use report instead of tabulate and get the bonus of an output table                                                      
                                                                                                                             
      Two solutions                                                                                                          
                                                                                                                             
         a. proc report (with USEFUL bonus table - sas dataset)                                                              
         b. proc tabulate (you have to transpose the output table - summary is faster)                                       
                                                                                                                             
                                                                                                                             
    github                                                                                                                   
    https://tinyurl.com/y5p2oezy                                                                                             
    https://github.com/rogerjdeangelis/utl-use-report-instead-of-tabulate-and-get-the-bonus-of-an-output-table               
                                                                                                                             
    SAS Forum                                                                                                                
    https://tinyurl.com/yxw6ep57                                                                                             
    https://communities.sas.com/t5/SAS-Procedures/proc-tabulate-producing-count-instead-of-sum/m-p/571389                    
                                                                                                                             
    *_                   _                                                                                                   
    (_)_ __  _ __  _   _| |_                                                                                                 
    | | '_ \| '_ \| | | | __|                                                                                                
    | | | | | |_) | |_| | |_                                                                                                 
    |_|_| |_| .__/ \__,_|\__|                                                                                                
            |_|                                                                                                              
    ;                                                                                                                        
                                                                                                                             
    SASHELP.CLASS total obs=19                                                                                               
                                                                                                                             
    Obs    NAME       SEX    AGE    HEIGHT    WEIGHT                                                                         
                                                                                                                             
      1    Alfred      M      14     69.0      112.5                                                                         
      2    Alice       F      13     56.5       84.0                                                                         
      3    Barbara     F      13     65.3       98.0                                                                         
      4    Carol       F      14     62.8      102.5                                                                         
      5    Henry       M      14     63.5      102.5                                                                         
      6    James       M      12     57.3       83.0                                                                         
    ....                                                                                                                     
                                                                                                                             
                                                                                                                             
    *            _               _                                                                                           
      ___  _   _| |_ _ __  _   _| |_                                                                                         
     / _ \| | | | __| '_ \| | | | __|                                                                                        
    | (_) | |_| | |_| |_) | |_| | |_                                                                                         
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                        
                    |_|                                                                                                      
    ;                                                                                                                        
                                                                                                                             
    * REPORT;                                                                                                                
    * BONUS TABLE (you can eeasily add gridlines and a box with a style)                                                     
                                                                                                                             
                                                                                                                             
           _Weight by Sex Age__                                                                                              
                                                                                                                             
                   F          M                                                                                              
     AGE                                                                                                                     
                                                                                                                             
      11       50.5         85                                                                                               
      12      161.5      310.5                                                                                               
      13        182         84                                                                                               
      14      192.5        215                                                                                               
      15      224.5        245                                                                                               
      16          .        150                                                                                               
                                                                                                                             
                                                                                                                             
                                                                                                                             
    WANT total obs=6                                                                                                         
                                                                                                                             
      AGE      F        M                                                                                                    
                                                                                                                             
       11     50.5     85.0                                                                                                  
       12    161.5    310.5                                                                                                  
       13    182.0     84.0                                                                                                  
       14    192.5    215.0                                                                                                  
       15    224.5    245.0                                                                                                  
       16       .     150.0                                                                                                  
                                                                                                                             
                                                                                                                             
    * TABULATE;                                                                                                              
                                                                                                                             
                                                                                                                             
    --------------------------------                                                                                         
    |    |           SEX           |                                                                                         
    |    |-------------------------|                                                                                         
    |    |     F      |     M      |                                                                                         
    |    |------------+------------|                                                                                         
    |    |   WEIGHT   |   WEIGHT   |                                                                                         
    |    |------------+------------|                                                                                         
    |    |    Sum     |    Sum     |                                                                                         
    |----+------------+------------|                                                                                         
    |AGE |            |            |                                                                                         
    |----|            |            |                                                                                         
    |11  |       50.50|       85.00|                                                                                         
    |----+------------+------------|                                                                                         
    |12  |      161.50|      310.50|                                                                                         
    |----+------------+------------|                                                                                         
    |13  |      182.00|       84.00|                                                                                         
    |----+------------+------------|                                                                                         
    |14  |      192.50|      215.00|                                                                                         
    |----+------------+------------|                                                                                         
    |15  |      224.50|      245.00|                                                                                         
    |----+------------+------------|                                                                                         
    |16  |           .|      150.00|                                                                                         
    --------------------------------                                                                                         
                                                                                                                             
                                                                                                                             
    WORK.WANTAB total obs=11                                                                                                 
                                                                                                                             
                     WEIGHT_                                                                                                 
       AGE    SEX      SUM                                                                                                   
                                                                                                                             
        11     F       50.5                                                                                                  
        11     M       85.0                                                                                                  
        12     F      161.5                                                                                                  
        12     M      310.5                                                                                                  
        13     F      182.0                                                                                                  
        13     M       84.0                                                                                                  
        14     F      192.5                                                                                                  
        14     M      215.0                                                                                                  
        15     F      224.5                                                                                                  
        15     M      245.0                                                                                                  
        16     M      150.0                                                                                                  
                                                                                                                             
    *          _       _   _                                                                                                 
     ___  ___ | |_   _| |_(_) ___  _ __  ___                                                                                 
    / __|/ _ \| | | | | __| |/ _ \| '_ \/ __|                                                                                
    \__ \ (_) | | |_| | |_| | (_) | | | \__ \                                                                                
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|___/                                                                                
                                                                                                                             
    ;                                                                                                                        
                                                                                                                             
    *                          _                                                                                             
     _ __ ___ _ __   ___  _ __| |_                                                                                           
    | '__/ _ \ '_ \ / _ \| '__| __|                                                                                          
    | | |  __/ |_) | (_) | |  | |_                                                                                           
    |_|  \___| .__/ \___/|_|   \__|                                                                                          
             |_|                                                                                                             
    ;                                                                                                                        
                                                                                                                             
                                                                                                                             
    proc report data=sashelp.class nowd missing                                                                              
            out=want(rename=(_c2_=F _C3_=M) drop=_break_) headskip;                                                          
                                                                                                                             
      cols age ("_Weight by Sex Age_" sex, weight) ;                                                                         
                                                                                                                             
        define age / group;                                                                                                  
        define sex /group across "";                                                                                         
        define weight / "" display sum;                                                                                      
                                                                                                                             
    run;quit;                                                                                                                
                                                                                                                             
    *_        _           _       _                                                                                          
    | |_ __ _| |__  _   _| | __ _| |_ ___                                                                                    
    | __/ _` | '_ \| | | | |/ _` | __/ _ \                                                                                   
    | || (_| | |_) | |_| | | (_| | ||  __/                                                                                   
     \__\__,_|_.__/ \__,_|_|\__,_|\__\___|                                                                                   
                                                                                                                             
    ;                                                                                                                        
                                                                                                                             
    proc tabulate data=SASHELP.CLASS out=wantab(drop=_:);                                                                    
      class age sex;                                                                                                         
      var weight;                                                                                                            
      table age, sex*weight*sum/rts=6;                                                                                       
    run;                                                                                                                     
                                                                                                                             
                                                                                                                             
                                                                                                                             
