# Kafka Visualizer

```sh
docker compose up kubefwd -d
# Wait a few seconds for it to initialize
docker compose up kowl
```

This project get's it protobuf messages from [stream-data](https://github.com/FigureTechnologies/stream-data). If you want to declare your own messages for topics, you will add them to the `proto` folder. However, both the filesystem and git can not currently be enabled together.

Each proto message will need to manually be mapped to a topic like this:

```yaml
- topicName: profile
  valueProtoType: profile.Profile
  keyProtoType: UUID
```

## Known Issues
`kubefwd` timesout sometimes. The solution is to "down" everything and repeat the startup process.