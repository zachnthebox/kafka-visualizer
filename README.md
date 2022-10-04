# Kafka Visualizer

## Tools Used

- [Kowl](https://github.com/cloudhut/kowl)
- [Kubefwd](https://github.com/txn2/kubefwd)

## About

This repo allows you to read data from a topic in kafka and see the actual proto message in JSON form.

The protobuf messages from [stream-data](https://github.com/FigureTechnologies/stream-data).
If you want to declare your own messages for topics, you will add them to the `proto` folder. 
However, both the filesystem and git can not currently be enabled together.

## Setup

~~Kowl is setup to use a `GITHUB_TOKEN` environment variable from the HOST machine.
It is used to clone `stream-data`.
This will need to be setup prior to "up"ing~~

Although hooking stream data with GIT up works, it was not the best integration.
There inveitably needs to be external protos required outside of the GIT repo, but there is no way to use more than one GIT repo or use GIT and file based protos.
If I want to look at properties for a proto, I copy the necessary protos in a proto folder.

Currently, each proto message will need to manually be mapped to a topic.
If we are able to use the schema registry from Confluent Cloud, the git integration and topic mapping would not be required here.
The registry would take care of all of that.

```yaml
- topicName: profile
  valueProtoType: profile.Profile
  keyProtoType: UUID
```

## Usage

```sh
docker compose up
```

Kowl will be accessible here - http://localhost:8081
