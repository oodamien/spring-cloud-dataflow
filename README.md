<p align="center">
  <a href="https://cloud.spring.io/spring-cloud-dataflow/">
    <img alt="Spring Data Flow Dashboard" title="Spring Data Flow" src="https://i.imgur.com/hpeKaRk.png" width="450" />
  </a>
</p>

<p align="center">
  <a href="http://cloud.spring.io/spring-cloud-dataflow/#quick-start">
    <img src="https://spring.io/badges/spring-cloud-dataflow/ga.svg"
         alt="Latest Release Version" />
  </a>
  <a href="http://cloud.spring.io/spring-cloud-dataflow/#quick-start">
    <img src="https://spring.io/badges/spring-cloud-dataflow/snapshot.svg"
         alt="Latest Snapshot Version" />
  </a>
  <a href="https://codecov.io/gh/spring-cloud/spring-cloud-dataflow/branch/master">
    <img src="https://codecov.io/gh/spring-cloud/spring-cloud-dataflow/branch/master/graph/badge.svg"
         alt="Codecov" />
  </a>
  <br>
  <a href="https://build.spring.io/browse/SCD-BMASTER">
    <img src="https://build.spring.io/plugins/servlet/wittified/build-status/SCD-BMASTER"
         alt="Build Status" />
  </a>
  <a href="http://waffle.io/spring-cloud/spring-cloud-dataflow">
    <img src="https://badge.waffle.io/spring-cloud/spring-cloud-dataflow.svg?label=ready&title=Ready"
         alt="Stories Ready" />
  </a>
  <a href="http://waffle.io/spring-cloud/spring-cloud-dataflow">
    <img src="https://badge.waffle.io/spring-cloud/spring-cloud-dataflow.svg?label=In%20Progress&title=In%20Progress"
         alt="Stories In Progress" />
  </a>

</p>

<p align="center">
  <a href="#introduction">Introduction</a> •
  <a href="#how-to-use">How To Use</a> •
  <a href="#features">Features</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#reporting-issues">Reporting Issues</a>
</p>

## Introduction

**Spring Cloud Data Flow** is a toolkit for building data integration and real-time data processing pipelines. 

Pipelines consist of Spring Boot apps, built using the 
[Spring Cloud Stream](https://github.com/spring-cloud/spring-cloud-stream)
or [Spring Cloud Task](https://github.com/spring-cloud/spring-cloud-task) microservice frameworks. 

This makes **Spring Cloud Data Flow** suitable for a range of data processing use cases, from import/export to 
event streaming and predictive analytics.

---

## How To Use

Please ensure that at a minimum [Maven](http://maven.apache.org/) and [Git](https://git-scm.com/) are available on your system (Using [Maven](http://maven.apache.org/) is also the easiest route for Java developers to get started).

	$ git clone https://github.com/spring-cloud/spring-cloud-dataflow.git
	$ cd spring-cloud-dataflow
	$ ./mvnw clean install

For more information on building, see this [link](https://github.com/spring-cloud/spring-cloud-dataflow/blob/master/spring-cloud-dataflow-docs/src/main/asciidoc/appendix-building.adoc).

**Building on Windows**

When using Git on Windows to check out the project, it is important to handle line-endings correctly during checkouts. By default Git will change the line-endings during checkout to `CRLF`. This is, however, not desired for _**Spring Cloud Data Flow**_ as this may lead to test failures under Windows.

Therefore, please ensure that you set Git property `core.autocrlf` to `false`, e.g. using: `$ git config core.autocrlf false`. Fore more information please refer to the [Git documentation, Formatting and Whitespace](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration).

---

## Features

The [Core](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-core)
domain module includes the concept of a **stream** that is a composition of spring-cloud-stream
modules in a linear pipeline from a **source** to a **sink**, optionally including **processor** application(s)
in between. The domain also includes the concept of a **task**, which may be any process that does
not run indefinitely, including [Spring Batch](https://github.com/spring-projects/spring-batch) jobs.

The [App Registry](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-registry)
maintains the set of available apps, and their mappings to URIs.
For example, if relying on Maven coordinates, an app's URI would be of the format:
`maven://<groupId>:<artifactId>:<version>`

The **Data Flow Server** is a Spring Boot application that provides a common REST API and UI. For each
runtime environment there is a different version of the **Data Flow Server** that depends upon a
deployer SPI implementation for that environment. The github locations for these Data Flow Servers are:

* [Local](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-server-local)
* [Cloud Foundry](https://github.com/spring-cloud/spring-cloud-dataflow-server-cloudfoundry)
* [Kubernetes](https://github.com/spring-cloud/spring-cloud-dataflow-server-kubernetes)
* [Apache YARN](https://github.com/spring-cloud/spring-cloud-dataflow-server-yarn)
* [Apache Mesos](https://github.com/spring-cloud/spring-cloud-dataflow-server-mesos)

_There are also community maintained **Spring Cloud Data Flow** implementations for Hashicorp's [Nomad](https://github.com/donovanmuller/spring-cloud-dataflow-server-nomad) and RedHat's [Openshift](https://github.com/donovanmuller/spring-cloud-dataflow-server-openshift)._

The deployer SPI mentioned above is defined within the [Spring Cloud Deployer](https://github.com/spring-cloud/spring-cloud-deployer)
project. That provides an abstraction layer for deploying the apps of a given stream or task and managing their lifecycle.
The github locations for the corresponding **pring Cloud Deployer** SPI implementations are:

* [Local](https://github.com/spring-cloud/spring-cloud-deployer-local)
* [Cloud Foundry](https://github.com/spring-cloud/spring-cloud-deployer-cloudfoundry)
* [Kubernetes](https://github.com/spring-cloud/spring-cloud-deployer-kubernetes)
* [Apache YARN](https://github.com/spring-cloud/spring-cloud-deployer-yarn)
* [Apache Mesos](https://github.com/spring-cloud/spring-cloud-deployer-mesos)

**Interfaces**

The [Shell](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-shell)
connects to the **Data Flow Server**'s REST API and supports a DSL that simplifies the process of
defining a stream or task and managing its lifecycle.

The [Dashboard](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-ui)
provides an UI. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor 
incididunt ut labore et dolore magna aliqua.

---

## Contributing

We welcome contributions! Follow this [link](https://github.com/spring-cloud/spring-cloud-dataflow/blob/master/spring-cloud-dataflow-docs/src/main/asciidoc/appendix-contributing.adoc) for more information on how to contribute.


---

## Reporting Issues

When reporting problems, it'd be helpful if the bug report includes the details listed on this [wiki-article](https://github.com/spring-cloud/spring-cloud-dataflow/wiki/Reporting-Issues). 