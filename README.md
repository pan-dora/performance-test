## Distributed Load Testing with Kubernetes in Google Cloud

### JMeter on using the fcrepo-base ["Number of Containers"](https://wiki.duraspace.org/display/FF/Performance+and+Scalability+Test+Plans#PerformanceandScalabilityTestPlans-Test4-Numberofcontainers-default) Test Plan

#### Example Command
`./jmeter -Gfedora_4_server=10.0.2.6 -Gfedora_4_context=fcrepo/rest -Gcontainer_threads=1 -l perf.log -n -t fedora-base.jmx -R10.0.1.4,10.0.2.7`

This is a short run for proof of concept.  See `log` directory for output.

This concept demonstrates that the peformance threshold tests can scale so that test times (and one time costs) can be greatly reduced.

It also demonstrates the potential for CI build triggers to create and push docker images that can be readily deployed to a Kubernetes cluster for performance analysis.