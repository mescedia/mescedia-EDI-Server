# about 

  mescedia is a ready to use edi server (https://en.wikipedia.org/wiki/Electronic_data_interchange)
  for processing most common edi messages formats such as CSV, XML, UN/EDIFACT, ... using open standards.

  It is build upon existing powerful, production proved open source frameworks and libraries so it is not a new invetion.

 
# setup

  make sure you've downloaded and installed the smooks/unedifact project correctly ( -> https://github.com/smooks/unedifact).
  
  to build the server run:

	$ mvn clean install 

  change to karaf-root
	
	$ cd mescedia/ 

  to start karaf  

	in console: 		$ bin/karaf 
	or  in background: 	$ bin/start  

  watch the data log for detailed information: 
	
	$ tail -f data/log/karaf.log  
  
  
# examples
  
  This setup includes the following example szenarios :

  A retailers ERP imports INVOIC and exports ORDERS messages in CSV format. 
  His suppliers ERP on this other hand XML messages. Both retailer and supplier 
  exchange UN/EDIFACT (D96A) messages. 

	Supplier (XML) 		UN/EDIFACT			Retailer (CSV)
	-------------------------------------------------------
	ORDERS.xml   < 		ORDERS.edi  <    	ORDERS.csv
	INVOIC.xml   > 		INVOIC.edi  > 		INVOIC.csv

	You may refer to the corresponding camel-routes ($karaf.home/deploy/edi-routes.xml) and the contents of the 
	$karaf.home/mapping folder in order to understand how the message transformation works. 
		
    The testfiles (ORDRES.csv and INVOIC.xml) resist in $karaf.home/testfiles/ folder. 
    Copy them to their corresponding inbound destinations (CAMEL_FS/ORDERS_CSV_IN and CAMEL_FS/INVOIC_XML_IN) and watch 
    the data logs and output folders for results. 
  
   In order to get the full picture you might refer to the subprojects websites: 

   	Apache-Karaf - [a link]https://karaf.apache.org/
   	Apache-Camel - [a link]https://camel.apache.org/
   	Smooks       - [a link]http://www.smooks.org 

   or visit project website at https://www.mescedia.com
   and/or the page of recommended resources: https://www.mescedia.com/recommendations

enjoy
