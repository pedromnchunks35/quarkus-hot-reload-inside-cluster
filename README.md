# Info
- A small project for understanding how can i live code with quarkus..
- In resources we change the application.properties to open the port for the live coding
- We will simply create a pod that exposes those ports out for us in the exterior
  - For this we will create a image that has java 17 installed to run our jar that will be mapped here
  - The config is in the kubernetes image
  - Remmeber that we builded the quarkus app using `mvn package`, so we just need to run the java app inside of target/quarkus-app/quarkus-run.jar
- We must pass a env variable like: 
  ```
  - name: QUARKUS_LAUNCH_DEVMODE 
    value: "true"
  ```
- After everything just use `mvn quarkus:remote-dev`
- After that we can test it using:
  ```
    grpcurl -plaintext -d '{"name": "Alice"}' 172.24.166.62:30001 hello.HelloGrpc/SayHello
  ```
- Check the resources for more info
  ```
  quarkus.package.jar.type=mutable-jar
  quarkus.http.host=0.0.0.0
  quarkus.live-reload.password=12341234
  quarkus.live-reload.url=http://172.24.166.62:30000
  quarkus.profile=dev
  quarkus.grpc.server.port=2040
  ```  
- we should get something like this as config
- We configed the host acceptance
- The profile we config for dev
- We config also the grpc port for the server because it was with conflits
- Only the password the url for live-reload are for the client when we use the mvn quarkus:remote-dev