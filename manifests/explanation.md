## K8s Deployment
  ## Steps
  1. Create manifests folder
  2. Built existiong Dockerfile containers (front end and backend) and pushed to dockerhub
      
      ```
      docker build -t mattwanjau/yolo-backend:v2.0.0 backend/
      docker push mattwanjau-yolo-backend:v2.0.0
      ```
  2. Create manifests files

      * mongodb-service.yaml - to create the headless mongo db service
      * mongodb-statefulset.yaml -Stateful set for mongo db
      * client-deployment.yaml - describes  our deployment nodes for `mattwanjau/yolo-client:V2.0.0` container(s)
      * client-service.yml - specifies a port to access the client
      * backend-deployment.yaml - describes  our deployment for `mattwanjau/yolo-backend:V2.0.0` container(s)
      * backend-service.yaml - specifies a port to access the backend

  3. Use kubectl to apply files 
     * Apply mongodb-service.yaml
        ```
        kubectl apply -f manifests/mongodb-service.yaml
        ```
        run `kubectl get svc` to verifyservice mongo db has been created
     * Apply mongodb-statefulset.yaml to create stateful pod (single).
        ```
        kubectl apply -f manifests/mongodb-statefulset.yaml
        ```
       run   `kubctl get pv` to verify existence of persistene volume
     *  Apply  both deployment and service files
        ```
        kubectl apply -f manifests/backend-service.yaml 
        kubectl apply -f manifests/backend-deployment.yaml
        kubectl apply -f manifests/client-service.yaml 
        kubectl apply -f manifests/client-deployment.yaml
        ```

  Service  Creation  Links\
        ```
                    NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)          AGE
                    kubernetes             ClusterIP      10.20.0.1     <none>          443/TCP          23h
                    mongodb                ClusterIP      None          <none>          27017/TCP        15h
                    yolo-backend-service   LoadBalancer   10.20.15.92   34.91.142.200   5000:30892/TCP   15h
                    yolo-client-service    LoadBalancer   10.20.13.59   34.32.244.73    3000:32367/TCP   14h
        ```
 \ Frontend\
34.32.244.73\
       
      
