# Java SDK for CloudEvents API

[![Build Status](https://travis-ci.org/cloudevents/sdk-java.png)](https://travis-ci.org/cloudevents/sdk-java)
[![License](https://img.shields.io/:license-Apache2-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/io.cloudevents/cloudevents-parent/badge.svg)](https://maven-badges.herokuapp.com/maven-central/io.cloudevents/cloudevents-parent)
[![Javadocs](http://www.javadoc.io/badge/io.cloudevents/cloudevents-api.svg?color=green)](http://www.javadoc.io/doc/io.cloudevents/cloudevents-api)

A Java API for the [CloudEvents specification](https://github.com/cloudevents/spec)

## Motivation

The [CloudEvents specification](https://github.com/cloudevents/spec) is vendor-neutral specification for defining the format of event data that is being exchanged between different cloud systems. The specification basically defines an abstract envelope for any event data payload, without knowing specific implementation details of the actual underlying event. The current version of the spec is at `0.2` and it describes a simple event format, which was demonstrated at last [KubeCon 2018](https://youtu.be/TZPPjAv12KU) using different _Serverless platforms_, such as [Apache Openwhisk](https://github.com/apache/incubator-openwhisk).

## Java API

Based on the specification we started to look at an early implementation of the API for Java. Using the API your backend application can create strongly-typed CloudEvents, such as:

```java
// given
final String eventId = UUID.randomUUID().toString();
final URI src = URI.create("/trigger");
final String eventType = "My.Cloud.Event.Type";
final MyCustomEvent payload = ...

// passing in the given attributes
final CloudEvent<MyCustomEvent> cloudEvent = new CloudEventBuilder<MyCustomEvent>()
    .type(eventType)
    .id(eventId)
    .source(src)
    .data(payload)
    .build();
```

## Possible Integrations

The idea on the API is to keep the pure API simple, for allowing a wide range of possible integrations

* [CDI](cdi/)
* [Eclipse Vert.x](http/vertx/)
