# GenerateAvroData
Step 1: Create a schema for your data manually as shown below and save it as .avsc file "employee.asvc"

{ "type": "record",
  "name": "Employee_Record",
  "namespace": "example.avro",
  "fields" : [
              {"name": "name", "type": "string"},
              {"name": "joining_date", "type": "string"},
              {"name": "role", "type": "string"},
              {"name": "dept", "type": ["null", "string"]},
              {"name": "salary", "type": "float"}
             ]
}

Step 2: Download avro tools jar file 

wget http://mirrors.sonic.net/apache/avro/avro-1.7.7/java/avro-tools-1.7.7.jar

Step 3: Generate .java file for the schema using the jar file downloaded

java -jar avro-tools-1.7.7.jar compile schema employee.asvc employee.java

Step 4: Open eclipse and create a maven project and add avro dependency along with MR dependency in pom.xml
    <dependency>
		  <groupId>org.apache.avro</groupId>
		  <artifactId>avro</artifactId>
		  <version>1.7.7</version>
	  </dependency>
	  
Step 5: create two classes one for the .java file generated i.e., Employee_Record.java for the schema and another to provide
data which you can see in src/main/java/Avro.GenerateAvro/GenerateDataWithCode.java and run it it generates employee.avro file

Step 6: copy the .avro file to HDFS to use it with HIVE/PIG

