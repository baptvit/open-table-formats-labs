docker build . -t xtable

docker run \
  -v ./xtable/config.yml:/xtable/config.yml \
  -v ./xtable/core-site.xml:/xtable/core-site.xml \
  -v ./xtable/catalog.yml:/xtable/catalog.yml \
  xtable \
  --datasetConfig /xtable/config.yml --hadoopConfig /xtable/core-site.xml --icebergCatalogConfig xtable/catalog.yml


docker run \
  -v ./manifests/hello-world.yml:/xtable/hello-world.yml \
  -v /tmp/hudi-dataset/people:/tmp/hudi-dataset/people:rw \
  xtable \
  --datasetConfig /xtable/hello-world.yml


java -jar /home/baptvit/Documents/github/lakehouse-labs/xtable/incubator-xtable/xtable-utilities/target/xtable-utilities_2.12-0.2.0-SNAPSHOT-bundled.jar --datasetConfig ./manifests/hello-world.yml

docker run -it \
  -v ./manifests/hello-world.yml:/xtable/hello-world.yml \
  -v /home/baptvit/Documents/github/lakehouse-labs/notebooks/warehouse/hudi/hudi_db.db/accounts_xtable:/home/baptvit/Documents/github/lakehouse-labs/notebooks/warehouse/hudi/hudi_db.db/accounts_xtable \
  xtable \
  /bash



  pyspark \
  --packages org.apache.hudi:hudi-spark3.5-bundle_2.12:0.15.0 \
  --conf "spark.serializer=org.apache.spark.serializer.KryoSerializer" \
  --conf "spark.sql.catalog.spark_catalog=org.apache.spark.sql.hudi.catalog.HoodieCatalog" \
  --conf "spark.sql.extensions=org.apache.spark.sql.hudi.HoodieSparkSessionExtension"


  Xtable limitations with 1.0.0 HUDI versions