## Analyzing Cloudfront Logs with Google BigQuery

Why BigQuery not Redshit? Because BQ is lot cheaper for our workload!

### Setup

1. Setup Cloudfront
  1. Enable Cloudfront logs (of course!)
  2. Update `s3` section of the Logstash config. Point to the bucket where Cloudfront logs will be stored.

2. Setup Google BigQuery dataset
  1. Go to https://console.developers.google.com/apis/credentials and add a new Service Account. Download the key file.
  2. Create a BigQuery dataset.
  3. Update `google_bigquery` section of the Logstash config.

3. Setup a Logstash node
  1. Install Logstash 2.x. This is a pretty good guide if you're using Ubuntu https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04. No need to install Elasticsearch.
  2. Install google_bigquery Logstash output plugin. See https://www.elastic.co/guide/en/logstash/current/plugins-outputs-google_bigquery.html.
  3. Copy the Google Cloud key file and the Logstash configuration file. `/etc/logstash/conf.d/` is the best place.

That's it. New BigQuery tables will be created every hour.