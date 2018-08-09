# Tensorflow-datalab-dataproc

To revert your SDK to the previously installed version, you may run:
  $ gcloud components update --version 148.0.0


gcloud dataproc cluster create model-6  --initialization-actions gs://<GCS_BUCKET>/datalab/datalab.sh  --scopes cloud-platform


gcloud beta dataproc clusters create model-6 --max-idle=2h  ^
--subnet default --zone us-east1-c ^
--metadata "JUPYTER_CONDA_PACKAGES=numpy:pandas:scikit-learn" ^
--project mortgage-data-warehouse ^
--master-machine-type n1-standard-16 --master-boot-disk-size 500 ^
--num-workers 2 --worker-machine-type n1-highmem-32 --worker-boot-disk-size 500 ^
--scopes https://www.googleapis.com/auth/cloud-platform ^
--properties spark:spark.executorEnv.PYTHONHASHSEED=0,spark:spark.yarn.am.memory=2048m ^
--initialization-actions ^
gs://dataproc-initialization-actions/jupyter/jupyter.sh,^
gs://dataproc-initialization-actions/conda/bootstrap-conda.sh,^
gs://dataproc-initialization-actions/conda/install-conda-env.sh,^
gs://dataproc-initialization-actions/datalab/datalab.sh,^
gs://dataproc-initialization-actions/zeppelin/zeppelin.sh --metadata=zeppelin-port=8082




gcloud beta dataproc clusters create model-6 --max-idle=3h  ^
--image-version 1.1 ^
--subnet default --zone us-east1-c ^
--project mortgage-data-warehouse ^
--master-machine-type n1-standard-4 --master-boot-disk-size 50 ^
--num-workers 4 --worker-machine-type n1-standard-2 --worker-boot-disk-size 50 ^
--scopes https://www.googleapis.com/auth/cloud-platform ^
--initialization-actions ^
gs://dataproc-initialization-actions/zeppelin/zeppelin.sh

gs://mortgage-data-warehouse/dataproc-initialization-actions/zeppelin/zeppelin.sh


n1-highmem-2  n1-standard-2


## ADD DEPENDENCIES artifact to spark ( com.databricks:spark-csv_2.11:1.5.0 )
                                     com.spotify:spark-bigquery_2.11:0.2.1

%sh echo 'export SPARK_SUBMIT_OPTIONS="--packages com.spotify:spark-bigquery_2.11:0.2.0"' >> /usr/lib/zeppelin/conf/zeppelin-env.sh




datalab create --zone us-east1-c --machine-type n1-highmem-64  balab

datalab connect --zone us-east1-c balab




gcloud compute copy-files model-6-m:../../datalab/notebooks/FHLMC.ipynb  ./Documents/Notebooks

