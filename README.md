# RandomNumberMCP

An MCP (Model Context Protocol) server built with C# that provides random number generation capabilities.

## Features

- **Random Number Generation**: Generate random numbers within specified ranges
- **Built with .NET 10**: Leverages the latest .NET runtime for performance and features
- **Self-Contained Deployment**: Single-file executables for all major platforms
- **Cross-Platform Support**: Pre-built for Windows, macOS, and Linux

## Supported Platforms

The MCP server is built as self-contained applications for:
* Windows x64 (`win-x64`)
* Windows ARM64 (`win-arm64`)
* macOS ARM64 (`osx-arm64`)
* Linux x64 (`linux-x64`)
* Linux ARM64 (`linux-arm64`)
* Linux musl x64 (`linux-musl-x64`)

## Installation

Install the package from NuGet:

```bash
dotnet tool install --global RandomNumberMCP
```

Or add it to your MCP configuration:

```json
{
  "servers": {
    "RandomNumberMCP": {
      "type": "stdio",
      "command": "RandomNumberMCP"
    }
  }
}
```

See [aka.ms/nuget/mcp/guide](https://aka.ms/nuget/mcp/guide) for the full guide.

## Checklist before publishing to NuGet.org

- [x] Test the MCP server locally using the steps below
- [x] Update the package metadata in the .csproj file
- [x] Update `.mcp/server.json` to declare the MCP server's inputs
- [ ] Pack the project using `dotnet pack`
- [ ] Publish to NuGet.org

For detailed guidance, see [aka.ms/nuget/mcp/guide](https://aka.ms/nuget/mcp/guide).

## Building for Release

Pack the project for NuGet distribution:

```bash
dotnet pack --configuration Release
```

The `bin/Release` directory will contain the package file (`.nupkg`), which can be [published to NuGet.org](https://learn.microsoft.com/en-us/nuget/nuget-org/publish-a-package).

## Developing Locally

To test this MCP server from source code (locally) without using a built MCP server package, you can configure your IDE to run the project directly using `dotnet run`.

```json
{
  "servers": {
    "RandomNumberMCP-Dev": {
      "type": "stdio",
      "command": "dotnet",
      "args": [
        "run",
        "--project",
        "<PATH TO PROJECT DIRECTORY>/RandomNumberMCP.csproj"
      ]
    }
  }
}
```

To run locally:

```bash
dotnet run
```

## Available Tools

### GetRandomNumber
Generates a random number between the specified minimum and maximum values.

**Parameters:**
- `min` (int, default: 0): Minimum value (inclusive)
- `max` (int, default: 100): Maximum value (exclusive)

**Returns:** A random integer in the range [min, max)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Resources

- [MCP Protocol Documentation](https://modelcontextprotocol.io)
- [Microsoft .NET Documentation](https://learn.microsoft.com/dotnet)
- [Model Context Protocol C# SDK](https://github.com/modelcontextprotocol/sdk-csharp)

## Using the MCP Server from NuGet.org

Once the MCP server package is published to NuGet.org, you can configure it in your preferred IDE. Both VS Code and Visual Studio use the `dnx` command to download and install the MCP server package from NuGet.org.

- **VS Code**: Create a `<WORKSPACE DIRECTORY>/.vscode/mcp.json` file
- **Visual Studio**: Create a `<SOLUTION DIRECTORY>\.mcp.json` file

For both VS Code and Visual Studio, the configuration file uses the following server definition:

```json
{
  "servers": {
    "MyMcpServer": {
      "type": "stdio",
      "command": "dnx",
      "args": [
        "<your package ID here>",
        "--version",
        "<your package version here>",
        "--yes"
      ]
    }
  }
}
```

## More information

.NET MCP servers use the [ModelContextProtocol](https://www.nuget.org/packages/ModelContextProtocol) C# SDK. For more information about MCP:

- [Official Documentation](https://modelcontextprotocol.io/)
- [Protocol Specification](https://spec.modelcontextprotocol.io/)
- [GitHub Organization](https://github.com/modelcontextprotocol)
- [MCP C# SDK](https://modelcontextprotocol.github.io/csharp-sdk)
