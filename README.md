OpenShift Go Cartridge
======================

Runs [JasperReports Server Pro](http://www.jaspersoft.com) on [OpenShift](https://openshift.redhat.com/app/login) using downloadable cartridge support.  

To install to OpenShift from the CLI (you'll need version 1.9 or later of rhc), run:

    rhc create-app jrs51 http://cartreflect-claytondev.rhcloud.com/reflect?github=smarterclayton/openshift-go-cart

When you push code to the repo, the cart will compile your package into $OPENSHIFT_REPO_DIR/bin/, with the last segment of the .godir being the name of the executable.  For the above .godir, your executable will be:

    $OPENSHIFT_REPO_DIR/bin/example

If you want to serve web requests (vs. running in the background), you'll need to listen on the ip address and port that OpenShift allocates - those are available as HOST and PORT in the environment.


Any log output will be generated to $OPENSHIFT_GO_DIR/logs/go.log


How it Works
------------

When you push code to your repo, a Git postreceive hook runs and invokes the bin/compile script.  This attempts to download a Go environment for you into $OPENSHIFT_GO_DIR/cache.  Once the environment is setup, the cart runs

    go get -tags openshift ./...

on a working copy of your source.  The main file that you run will have access to two environment variables, $HOST and $PORT, which contain the internal address you must listen on to receive HTTP requests to your application.


Credits
-------

The bin/compile script is based on the [Heroku Go buildpack](https://github.com/kr/heroku-buildpack-go), adapted for OpenShift cartridges.
