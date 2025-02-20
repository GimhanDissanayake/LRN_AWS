# Athena
======

1. Create an Athena database
- Settings Tab: 1st set up a query result location in Amazon S3
- Editor Tab: T create a database named mydatabase, enter the following CREATE DATABASE statement.
CREATE DATABASE mydatabase > Run
- Select the database from the dropdown

2. Create a table
Sample Data:
2014-07-05 20:00:09 DFW3 4260 10.0.0.15 GET testtest.cloudfront.net /test-image-1.jpeg 200 - Mozilla/5.0[...]
2014-07-05 20:00:09 DFW3 4252 10.0.0.15 GET testtest.cloudfront.net /test-image-2.jpeg 200 - Mozilla/5.0[...]
2014-07-05 20:00:10 AMS1 4261 10.0.0.15 GET testtest.cloudfront.net /test-image-3.jpeg 200 - Mozilla/5.0[...]

Mozilla/5.0%20(Android;%20U;%20Windows%20NT%205.1;%20en-US;%20rv:1.9.0.9)%20Gecko/2009040821%20IE/3.0.9

Statement:
CREATE EXTERNAL TABLE
- need to define:
    columns that map to the data
    how the data is delimited
    Amazon S3 location that contains the sample data

Ex:
CREATE EXTERNAL TABLE IF NOT EXISTS mytesttable1 (
  `Date` DATE,
  Time STRING,
  Location STRING,
  Bytes INT,
  RequestIP STRING,
  Method STRING,
  Host STRING,
  Uri STRING,
  Status INT,
  Referrer STRING,
  ClientInfo STRING
  ) 
  ROW FORMAT DELIMITED
  FIELDS TERMINATED BY '\t'
  LINES TERMINATED BY '\n'
  LOCATION 's3://test-cloudfront-distribution-logs/worpressmedia/';

Ex:
CREATE EXTERNAL TABLE IF NOT EXISTS mytesttable2 (
  `Date` DATE,
  Time STRING,
  Location STRING,
  Bytes INT,
  RequestIP STRING,
  Method STRING,
  Host STRING,
  Uri STRING,
  Status INT,
  Referrer STRING,
  os STRING,
  Browser STRING,
  BrowserVersion STRING
  ) 
  ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.RegexSerDe'
  WITH SERDEPROPERTIES (
  "input.regex" = "^(?!#)([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+([^ ]+)\\s+[^\(]+[\(]([^\;]+).*\%20([^\/]+)[\/](.*)$"
  ) LOCATION 's3://test-cloudfront-distribution-logs/worpressmedia/';

  Mozilla/5.0%20(X11;%20Linux%20x86_64)%20AppleWebKit/537.36%20(KHTML,%20like%20Gecko)%20Chrome/56.0.2924.87%20Safari/537.36%20Google%20(+https://developers.google.com/+/web/snippet/)	-	-	Hit	Gi0PibRF7l0wKcHSWd5Ij618SNqZNgQ8FgURDm8PRsA6_D3zCNxyVw==	d3d9xi60ak7z4l.cloudfront.net	http	361	0.003	-	-	-	Hit	HTTP/1.1	-	-	50748	0.001	Hit	text/html	134	-	-