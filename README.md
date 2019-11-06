# Elasticsearch-7-Update-
Elasticsearch Tomcat Logs. Cat


Install and Activate filebeat

curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.0-linux-x86_64.tar.gz

tar xzvf filebeat-7.3.1-linux-x86_64.tar.gz
7.4.0


edit filebeat.yml

./filebeat modules enable apache
./filebeat modules enable system


./filebeat setup --index-management -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["deves01:9500"]'

./filebeat setup -e -E output.logstash.enabled=false -E output.elasticsearch.hosts=['deves01:9500'] -E setup.kibana.host=devkib01.clacorp.com:10560

