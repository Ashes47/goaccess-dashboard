zcat

10 0 * * * zcat /opt/traefik/logs/access.log-$(date -d "yesterday" +\%Y\%m\%d).gz | docker exec -i goaccess-goaccess-1 goaccess --log-format='%h %l %u [%d:%t %^] "%r" %s %b "%R" "%u"' --date-format='%d/%b/%Y' --time-format='%H:%M:%S' --persist --restore --db-path=/db - > /dev/null 2>&1