// From F-ELK 8 super admin account not using for access to elastic
// require create service token for internal service for access

Step 1: Run elasticsearch image

Step 2: create service token for kibana
docker exec elasticsearch bin/elasticsearch-service-tokens create elastic/kibana kibana-token

Step 3: setup encrypt token for kibana (for create role & user) using openssl rand -hex 16
xpack.encryptedSavedObjects.encryptionKey = 

Step 4: Run kibana image with service token above
docker-compose up -d

Step 5: Create role logstash_writer and user logstash_internal  and cluster monitor
Create role : logstash_writer
 + Cluster privileges: monitor manage_index_template
 + Run As privileges: logstash_system
 + indicates: log-*
 + Privileges: create, write, index, create_index
 + 
Step 6: Config and run logstash 

Step 7: Config and run FileBeat


