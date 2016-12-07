# mco-dashboard
mco-dashboard - surveiller l'activité des bug tracker de ses clients avec kibana et elasticsearch

## Commandes docker pour exemple twitter
``` sh
docker run -it --rm --name logstash -v "$PWD":/config-dir logstash logstash -f /config-dir/logstash-twitter.conf


docker run -d -v "$PWD/elasticsearch/esdata":/usr/share/elasticsearch/data -p 9200:9200 -p 9300:9300 --name elasticsearch elasticsearch

Vérifier dans un navigateur : http://localhost:9200/_aliases
curl -XDELETE 'http://localhost:9200/anomalies-static/'
curl -XDELETE 'http://localhost:9200/anomalies-dynamic/'

docker run --link elasticsearch:elasticsearch -d --name kibana -p 5601:5601 kibana

```

## Commandes docker pour map demande
``` sh
cd /home/xavier/Documents/git-repository/mco-dashboard

docker run -it --rm --name logstash -v "$PWD":/config-dir logstash logstash -f /config-dir/logstash-csv.conf

docker run -it --rm --name logstash -v "$PWD":/config-dir logstash logstash -f /config-dir/logstash-static.conf

docker run -it --rm --name logstash -v "$PWD":/config-dir logstash logstash -f /config-dir/logstash-dynamic.conf


```

Pour ajouter une dernière colonne avec la date d'import :
sed 's/$/;2016-08-22 12:00:00/g' < 20160822-resultat.csv > toto.csv

:%s/$/;2016-08-22 12:00:00/

Change






