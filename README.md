mescedia :: Open Source EDI [![Version](https://img.shields.io/badge/Version-1.1.4-blue.svg)](https://github.com/mescedia/mescedia-edi-server)
============================


### about 

mescedia is an extensible, Java based EDI (https://en.wikipedia.org/wiki/Electronic_data_interchange) integration application
for processing most common EDI message formats such as UN/EDIFACT, CSV, XML, Fixed-Length, ... using open standards (XSLT, XQuery, Java, ...). It is build upon existing powerful, production proved Open Source frameworks and libraries such 
as: 

* *Apache-Karaf* :: https://karaf.apache.org
* *Apache-Camel* :: https://camel.apache.org
* *Smooks*       :: https://www.smooks.org


- - -
 
### prerequisites

1. Make sure that Java is properly installed and working.
2. Download and install the smooks/unedifact project -> https://github.com/smooks/unedifact.

### setup

To build the server run
	
	$ mvn clean install 

change to karaf-root 	

	$ cd karaf/ 

to start karaf run
  
	$ bin/karaf 	

install mescedia features in apache-karaf
	
	admin@edi-server $ feature:repo-add file:./mescedia-features.xml
	admin@edi-server $ feature:install mescedia  
  
  this might take a while ....  
  you may want to watch the data logs for detailed information during setup 
   
	$ tail -f data/log/karaf.log
	
  copy 'edi-routes.xml' to deploy folder before running the examples below

	$ cp ./edi-routes.xml ./deploy/  
  
- - -  
  
### examples

To start the server in background run  

	$ bin/start
 
This setup includes the data transformation mappings defining the following example szenarios:

A retailers ERP imports INVOIC and exports ORDERS messages in CSV format. 
The suppliers ERP on this other hand XML messages. Both retailer and supplier 
exchange UN/EDIFACT (D96A) messages. 

	Supplier (XML) 		UN/EDIFACT			Retailer (CSV)
	-------------------------------------------------------
	ORDERS.xml   < 		ORDERS.edi  <    	ORDERS.csv
	INVOIC.xml   > 		INVOIC.edi  > 		INVOIC.csv

You may refer to the corresponding camel-routes ($karaf.home/deploy/edi-routes.xml) and the contents of the 
$karaf.home/mapping folder in order to understand how the message transformation works. 
		
The testfiles (ORDERS.csv and INVOIC.xml) resist in $karaf.home/testfiles/ folder. 
Copy them to their corresponding inbound destinations (CAMEL_FS/ORDERS_CSV_IN and CAMEL_FS/INVOIC_XML_IN) and watch 
the data logs and output folders for results. 
 

enjoy

- - -