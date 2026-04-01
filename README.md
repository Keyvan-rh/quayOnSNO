# quayOnSNO
quay On single node openshift
Prep:
   1. Install LVM operator
   2. Create lvmcluster
   3. Install quay operator
   4. update config.yaml/ config_minio.yaml with correct values

INSTALLATION with local storage:
   1. oc login (to your OCP)
   2. oc new-project quay
   3. (optional) if you like to use minio (ext s3) use this and skip step 4.
        oc create secret generic --from-file config.yaml=./config_minio.yaml config-bundle-secret
   4. oc create secret generic --from-file config.yaml=./config.yaml config-bundle-secret
   5. oc apply -f quay.yaml 

NOTE:
This configuration works for Quay 3.11 and higher. You may need to adjust the CPU requests and limits to ensure compatibility with your system, as container timeouts are time-based and depend on CPU speed. For example, on an older Intel(R) Xeon(R) CPU E5-2650L v2 @ 1.70GHz, the settings for 4 CPUs work for Quay 3.11 but must be increased to 6 CPUs for Quay 3.17.
