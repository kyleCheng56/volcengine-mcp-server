# veDB MySQL MCP Server

This MCP server provides a tool to interact with the VolcEngine veDB MySQL Service, allowing you to search and retrieve knowledge from your collections.

## Features

- list_vedb_mysql_instances
> Retrieve a list of all veDB MySQL instances for the user, including a batch of instance IDs and basic information
- describe_vedb_mysql_detail
> Retrieve detailed information about a specific veDB MySQL instance
- list_vedb_mysql_instance_databases
> Retrieve a list of databases created in a specific veDB MySQL instance, including privileges info
- list_vedb_mysql_instance_accounts
> Obtain a list of accounts in a single veDB MySQL instance, with their privilege details
- modify_vedb_mysql_instance_alias
> Modify a specific veDB MySQL instance's alias

## Setup

### Prerequisites

- Python 3.10 or higher
- API credentials (AK/SK)

### Installation

1. Install the package:

```bash
pip install -e .
```

Or with uv (recommended):

```bash
uv pip install -e .
```

### Configuration

The server requires the following environment variables:

- `VOLC_ACCESSKEY`: Your VolcEngine access key
- `VOLC_SECRETKEY`: Your VolcEngine secret key
- `REGION`: Your VolcEngine region (e.g., "cn-beijing")

Optional environment variables:

- `PORT`: Port for the FastMCP server (default: 8000)

## Usage

### Running the Server

The server can be run with either stdio transport (for MCP integration) or SSE transport:

```bash
python -m mcp_server_vedb_mysql.server --transport stdio
```

Or:

```bash
python -m mcp_server_vedb_mysql.server --transport sse
```

## MCP Integration

To add this server to your MCP configuration, add the following to your MCP settings file:

```json
{
   "mcpServers": {
      "veDB_mysql": {
         "command": "uvx",
         "args": [
            "--from",
            "git+https://github.com/volcengine/mcp-server#subdirectory=server/mcp_server_vedb_mysql",
            "mcp-server-vedb-mysql"
         ],
         "env": {
            "VOLC_ACCESSKEY": "your-access-key",
            "VOLC_SECRETKEY": "your-secret-key",
            "REGION": "cn-beijing",
            "PORT": "8000",
            "ENDPOINT": "vedbm.cn-beijing.volcengineapi.com"
         }
      }
   }
}
```

## Troubleshooting

### Common Issues

1. **Authentication Errors**
   - Verify your AK/SK credentials are correct
   - Check that you have the necessary permissions for the collection

2. **Connection Timeouts**
   - Check your network connection to the VolcEngine API
   - Verify the host configuration is correct

3. **Empty Results**
   - Verify the collection name is correct
   - Try broadening your search query

### Logging

The server uses Python's logging module with INFO level by default. You can see detailed logs in `/tmp/mcp.vedbmysql.log` when running the server.

## Contributing

Contributions to improve the Viking Knowledge Base MCP Server are welcome. Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

Please ensure your code follows the project's coding standards and includes appropriate tests.

## License

volcengine/mcp-server is licensed under the [MIT License](https://github.com/volcengine/mcp-server/blob/main/LICENSE).
