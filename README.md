# EFK

Install and setup EFK: 

Step 1:- $ Start minikube

Step 2: Create an service file for elastic :

Then apply the yaml file:-
$ Kubectl apply -f file-svc.yaml

Step 3:- Let’s create the ElasticSearch statefulset now :

Then apply the yaml file :-
$ Kubectl apply -f file-sts.yaml

Step 4:- Verifying ElasticSearch Deployment:

$ kubectl port-forward 9200:9200 -n Out will be like:-

To check health of the elasticsearch:- $ curl http://localhost:9200/_cluster/health/?pretty

Step 5 : Create a manifest fluentd-role.yaml

Then apply the yaml file:-

$ kubectl apply -f fluentd-role.yaml

Step 6: let’s create a service.yaml for fluentd

Then apply the yaml file:-

$ kubectl apply -f fluentd-sa.yaml

Step 7 : let’s create a manifest for cluster rolebinding:

Then apply the yaml file:-

$ kubectl apply -f fluentd-rb.yaml

Step 8: let’s deploy the daemonset now :

Then apply the yaml file-:

$ kubectl apply -f fluentd-ds.yaml 

Step 9 : let’s create test-pod.yaml for verify the fluentd installation:

Then apply the yaml file :-

$kubectl apply -f test-pod.yaml

Step 10:- Now we are going to Deploy kibana deployment and service

Create the file- dep.yaml

Then apply the yaml file:-

$ kubectl apply -f file-dep.yaml

Step 11:- Now let’s create a service of type NodePort to access Kibana UI:

Then apply the yaml file:

$ kubectl apply -f file-svc.yaml

Step 12 :- Verifying Kibana Deployment

$ kubectl port-forward 5601:5601 -n After this access the UI through the browser $ curl http://localhost:5601/app/kibana

When your “Dashboard” is ready now you can configure your Kibana and check whether the logs are being picked up by fluentd and stored in elasticsearch or not(You can also use the sample logs/metrics/graphs and various logs available there).
