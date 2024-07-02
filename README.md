# quayOnSNO
quay On single node openshift
Prep:
   1. Install LVM operator
   2. Create lvmcluster
   3. Install quay operator

INSTALLATION with local storage:
   1. oc login (to your OCP)
   2. oc new-project quay
   3. oc create secret generic --from-file config.yaml=./config.yaml config-bundle-secret
   4. oc apply -f quay.yaml 

