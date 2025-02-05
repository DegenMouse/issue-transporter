# GitHub Issue Transporter

A command-line tool to transfer issues between GitHub repositories, preserving labels and maintaining parent-child relationships.

## Features

- Transfer single or multiple issues between repositories
- Preserve issue labels
- Maintain parent-child relationships between issues
- Support for both open and closed issues
- Automatic label creation in target repository

## Prerequisites

1. **Node.js and npm**
   - Install from [nodejs.org](https://nodejs.org/)

2. **GitHub CLI**
   - Install GitHub CLI following the [official instructions](https://github.com/cli/cli#installation)
   - Authenticate with GitHub:
     ```bash
     gh auth login
     ```
   - Follow the interactive prompts:
     - Select "GitHub.com"
     - Select "HTTPS"
     - Select "Y" for authentication with your GitHub credentials
     - Choose your preferred authentication method (browser or token)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/github-issue-transporter.git
   cd github-issue-transporter
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

## Usage

The basic command structure is:
```bash
node index.ts -- transfer <owner> <source-repo> <target-repo>
```


### Parameters

- `owner`: GitHub username or organization name
- `source-repo`: Name of the repository containing the issues
- `target-repo`: Name of the repository to transfer issues to

### Options

- `-a, --all`: Transfer all issues (both open and closed). Without this flag, only open issues are transferred.

### Examples

1. Transfer only open issues:
   ```bash
   npm start transfer octocat source-repo target-repo
   ```

2. Transfer all issues (open and closed):
   ```bash
   npm start transfer octocat source-repo target-repo --all
   ```

## Notes

- Both source and target repositories must be accessible to your GitHub account
- The GitHub CLI (`gh`) must be authenticated with appropriate permissions
- Labels will be automatically created in the target repository if they don't exist
- Parent-child relationships are preserved by transferring child issues first
- A brief delay is added between transfers to ensure GitHub API stability

## Troubleshooting

1. **Authentication Issues**
   - Ensure you're logged in to GitHub CLI:
     ```bash
     gh auth status
     ```
   - If not authenticated, run:
     ```bash
     gh auth login
     ```

2. **Permission Issues**
   - Verify you have write access to both repositories
   - Check your token permissions include repo access

3. **Rate Limiting**
   - If you hit rate limits, wait a few minutes before retrying
   - Consider using a Personal Access Token with higher rate limits

## License

MIT

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
