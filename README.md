# jboss-as-management

A Clojure wrapper around the JBoss AS7 "REST" management API.

## Usage

Right now, the support is fairly basic. You can check to see if the server is up,
shut it down, add a deployment, deploy said deployment, or remove said deployment.

You can also use the `api` function to call other management operations. It will
connect to whatever endpoint that `*api-endpoint*` is bound to, which is 
"http://localhost:9990/management" by default.

Examples:

    (require '[jboss-as.management :as mgt])

    ;;server representation
    (def server (mgt/create-server))

    ;; see if the server is up
    (mgt/ready? server)

    ;; deploy the content of some-descriptor-file
    (mgt/deploy server "my-deployment" (.toUrl some-descriptor-file))

    ;; check whether my-deployment is deployed
    (mgt/deployed? server "my-deployment")

    ;; undeploy the deployment
    (mgt/undeploy server "my-deployment")

    ;; shut it down, shut it down now
    (mgt/stop server)

## License

Copyright © 2012 Red Hat, Inc.

Distributed under the Eclipse Public License.
