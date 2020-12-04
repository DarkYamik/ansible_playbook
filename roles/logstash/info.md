sudo podman run -d  --name=logstash1 --volume /home/vagrant/config/:/usr/share/logstash/config:ro --volume /home/vagrant/pipeline:/usr/share/logstash/pipeline:ro --volume /var/log/containers:/usr/share/logstash/containers:ro docker.io/library/logstash:7.9.3

