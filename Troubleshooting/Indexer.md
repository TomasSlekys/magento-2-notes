# indexer:reindex errors

## Unknown filter type [phonetic] for [phonetic]

```console
Catalog Search index process error during indexation process:
{"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Unknown filter type [phonetic] for [phonetic]"}],"type":"illegal_argument_exception","reason":"Unknown filter type [phonetic] for [phonetic]"},"status":400}
```

Make sure that all required Elasticsearch plugins are installed and enabled. To check the installed plugins, run `curl -X GET "localhost:9200/_cat/plugins?v"`. If the `analysis-phonetic` plugin is not installed, install it by running `sudo bin/elasticsearch-plugin install analysis-phonetic`