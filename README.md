# 4.6


2.Problem Statement


1.If 7TB is the available disk space per node (9 disks with 1 TB, 2 disk for operating system etc. were excluded.). Assuming initial data size is 600 TB. How will you estimate the number of data nodes (n)?


2.Imagine that you are uploading a file of 500MB into HDFS.100MB of data is successfully uploaded into HDFS and another client wants to read the uploaded data while the upload is still in progress. What will happen in such a scenario, will the 100 MB of data that is uploaded will it be displayed?



Q1 solution :

This is the formula to estimate the number of data nodes (n): 

   n= H/d  
   
   where,
    d= disk space available per node.
    H= Hadoop storage
   
   but H=c*r*S/(1-i)
      
   Hence final formula to calculate number od data nodes is 
      
      n = c*r*S/(1-i)*d 

where 
  d= disk space available per node.
  c = average compression ratio. It depends on the type of compression used (Snappy, LZOP, ...) and size of the data. When no                 compression is used, c=1. 
  r = replication factor. It is usually 3 in a production cluster. 
  S = size of data to be moved to Hadoop. 
  i = intermediate factor. It is usually 1/3 or 1/4. Hadoop's working space dedicated to storing intermediate results of Map phases. 
  
  consider 
    c=1;
    r=3;
    i=1/4;
    S=600TB ...given
    d=7TB ...given
    
    Total no. of data nodes = 1*3*600/((1-1/4)*7) 
                            = 342.857 
                            = 343





Q2 Solution :


