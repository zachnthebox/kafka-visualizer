# Kafka Visualizer

## Tools Used

- [Kowl](https://github.com/cloudhut/kowl)
- [Kubefwd](https://github.com/txn2/kubefwd)

## About

This repo allows you to read data from a topic in kafka and see the actual proto message in JSON form.

The protobuf messages from [stream-data](https://github.com/FigureTechnologies/stream-data). If you want to declare your own messages for topics, you will add them to the `proto` folder. However, both the filesystem and git can not currently be enabled together.

## Setup

Kowl is setup to use a `GITHUB_TOKEN` environment variable from the HOST machine.
It is used to clone `stream-data`.
This will need to be setup prior to "up"ing

Each proto message will need to manually be mapped to a topic like this:

```yaml
- topicName: profile
  valueProtoType: profile.Profile
  keyProtoType: UUID
```

## Usage

```sh
docker compose up kubefwd -d
# Wait a few seconds for it to initialize
docker compose up kowl
```

## Known Issues

`kubefwd` timesout sometimes. The solution is to "down" everything and repeat the startup process.