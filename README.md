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

./filebeat setup -e -E output.logstash.enabled=false -E output.elasticsearch.hosts=['deves01:9500'] -E setup.kibana.host=devkib01:10560

sudo systemctl start filebeat
sudo systemctl enable filbeat

Logstash 

sudo vi /etc/logstash/conf.d/101-filebeat-input-file.conf
sudo vi /etc/logstash/conf.d/111-filebeat-filter-file.conf
sudo vi /etc/logstash/conf.d/121-filebeat-output-file.conf

Create a different input port number for each server that has a filebeat.. 

input {
  beats {
    port => 5044  
  }
}

test logstash pipleines 

sudo -u logstash /usr/share/logstash/bin/logstash --path.settings /etc/logstash -t
sudo systemctl start logstash
sudo systemctl enable logstash
