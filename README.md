# PROMETHEUS
1. wget https://github.com/prometheus/prometheus/releases/download/v2.22.2/prometheus-2.22.2.linux-amd64.tar.gz
2. tar -xvf prometheus-2.22.2.linux-amd64.tar.gz 
3. sudo useradd --no-create-home --shell /bin/false prometheus
4. sudo mkdir /etc/prometheus
5. sudo mkdir /var/lib/prometheus
6. sudo chown prometheus:prometheus /etc/prometheus
7. sudo chown prometheus:prometheus /var/lib/prometheus
8. cp prometheus-files/prometheus /usr/local/bin/
9. cp prometheus-files/promtool /usr/local/bin/
10. chown prometheus:prometheus /usr/local/bin/prometheus
11. chown prometheus:prometheus /usr/local/bin/promtool
12. cp -r prometheus-files/consoles /etc/prometheus
13. cp -r prometheus-files/console_libraries /etc/prometheus
14. chown -R prometheus:prometheus /etc/prometheus/consoles
15. chown -R prometheus:prometheus /etc/prometheus/console_libraries
16. vim /etc/prometheus/prometheus.yml
17. chown prometheus:prometheus /etc/prometheus/prometheus.yml
18. systemctl daemon-reload
19. systemctl start prometheus
20. systemctl status prometheus




# NODE_EXPORTER
1. cd /tmp
3. curl -LO https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz
5. tar -xvf node_exporter-0.18.1.linux-amd64.tar.gz
7. mv node_exporter-0.18.1.linux-amd64/node_exporter /usr/local/bin/
8. useradd -rs /bin/false node_exporter
9. vim /etc/prometheus/prometheus.yml
10. vim /etc/systemd/system/node_exporter.service
11. systemctl daemon-reload
12. systemctl start node_exporter
13. systemctl status node_exporter
14. systemctl restart prometheus
15. systemctl status prometheus




# ALERT_MANAGER
1. wget https://github.com/prometheus/alertmanager/releases/download/v0.21.0/alertmanager-0.21.0.linux-amd64.tar.gz
2. tar -xvf alertmanager-0.21.0.linux-amd64.tar.gz 
3. mkdir /usr/local/bin/alertmanager
4. cp -r alertmanager-0.21.0.linux-amd64/* /usr/local/bin/alertmanager/
5. vim /usr/local/bin/alertmanager/alertmanager.yml
6. vim /etc/prometheus/prometheus.yml
7. vim /etc/systemd/system/alertmanager.service
8. systemctl daemon-reload
9. systemctl restart alertmanager
10. systemctl status alertmanager
11. systemctl restart prometheus
12. systemctl status prometheus
