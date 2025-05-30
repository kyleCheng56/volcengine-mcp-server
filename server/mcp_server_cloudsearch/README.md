# MCP Server CloudSearch
| Version     | v1                                                                                                                                                                                |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description | Cloud Search is a fully managed service providing data search and analytics capabilities including full-text search, vector search, hybrid search, and spatio-temporal retrieval. |
| Category    | Database                                                                                                                                                                          |
| Tags        | ES，Elasticsearch，OpenSearch，Search                                                                                                                                                |

## Tools
This MCP Server product provides the following Tools:
### 1. cloudsearch_describe_zones
Query available zone list in a specified region
- Parameters:
  - `region_id`: region id

### 2. cloudsearch_describe_instance
Query the detail information of an instance
- Parameters:
  - `region_id`: region id
  - `instance_id`: instance id

### 3. cloudsearch_describe_instances
Query the instance list in a specified region
- Parameters:
  - `region_id`: region id
  - `zone_id`: zone id, support fuzzy query
  - `instance_id`: instance id, support fuzzy query
  - `instance_name`: instance name, support fuzzy query
  - `status`: instance status
  - `version`: instance version
  - `charge_type`: instance charge type
  - `project_name`: project name
  - `page_number`: page number
  - `page_size`: page size

### 4. cloudsearch_describe_instance_nodes
Query the node list of an instance
- Parameters:
  - `region_id`: region id
  - `instance_id`: instance id,

### 5. cloudsearch_describe_instance_plugins
Query the plugin list of an instance
- Parameters:
  - `region_id`: region id
  - `instance_id`: instance id

## Platform  
ark，python，cursor

## Service Link
https://console.volcengine.com/es/region:es+cn-beijing/v2/create?projectName=default

## Installation
Get ak/sk from [volcengine](https://www.volcengine.com/docs/6291/65568), then add ak/sk to the mcp server configuration, or configure it in the .env file in the working directory, the format is as follows

```shell
VOLC_ACCESSKEY=your_volcengine_ak
VOLC_SECRETKEY=your_volcengine_sk
```

## Using uv
Add the following configuration to your mcp settings file
```json
{
  "mcpServers": {
    "mcp-server-cloudsearch": {
      "command": "uvx",
      "args": [
        "--from",
        "git+https://github.com/volcengine/mcp-server.git#subdirectory=server/mcp_server_cloudsearch",
        "mcp-server-cloudsearch"
      ],
      "env": {
        "VOLC_ACCESSKEY": "your_volcengine_ak",
        "VOLC_SECRETKEY": "your_volcengine_sk"
      }
    }
  }
}
```
Or clone the repository to your local and start from the local code repository
```json
{
  "mcpServers": {
    "mcp-server-cloudsearch": {
      "command": "uv",
      "args": [
        "--directory",
        "path/to/src/mcp_server_cloudsearch",
        "run",
        "server.py"
      ],
      "env": {
        "VOLC_ACCESSKEY": "your_volcengine_ak",
        "VOLC_SECRETKEY": "your_volcengine_sk"
      }
    }
  }
}
```

## License
volcengine/mcp-server is licensed under the [MIT License](https://github.com/volcengine/mcp-server/blob/main/LICENSE).