# 区块链数据服务 

Vitruveo MCP Server 是一个为 Vitruveo 网络提供只读区块链服务的模型上下文协议服务器，适用于AI代理访问区块链数据。
Vitruveo MCP Server is a model context protocol server that provides read-only blockchain services for the Vitruveo network, suitable for AI agents to access blockchain data.## 工具列表 Tool List

本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。 本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。

| 工具 Tool   | 描述 Description         |
|-------|--------------------|
| get_core_contracts | Get core contract addresses |
| get_chain_info | Get information about an EVM network |
| get_supported_networks | Get a list of supported EVM networks |
| get_block_by_number | Get a block by its block number |
| get_latest_block | Get the latest block from the EVM |
| get_balance | Get the native token balance (ETH, MATIC, etc.) for an address |
| get_erc20_balance | Get the ERC20 token balance of an Ethereum address |
| get_token_balance | Get the balance of an ERC20 token for an address |
| get_transaction | Get detailed information about a specific transaction by its hash. Includes sender, recipient, value, data, and more. |
| get_transaction_receipt | Get a transaction receipt by its hash |
| estimate_gas | Estimate the gas cost for a transaction |
| read_contract | Read data from a smart contract by calling a view/pure function. This doesn't modify blockchain state and doesn't require gas or signing. |
| is_contract | Check if an address is a smart contract or an externally owned account (EOA) |
| get_token_info | Get comprehensive information about an ERC20 token including name, symbol, decimals, total supply, and other metadata. Use this to analyze any token on EVM chains. |
| get_token_balance_erc20 | Get ERC20 token balance for an address |
| get_nft_info | Get detailed information about a specific NFT (ERC721 token), including collection name, symbol, token URI, and current owner if available. |
| check_nft_ownership | Check if an address owns a specific NFT |
| get_erc1155_token_uri | Get the metadata URI for an ERC1155 token (multi-token standard used for both fungible and non-fungible tokens). The URI typically points to JSON metadata about the token. |
| get_nft_balance | Get the total number of NFTs owned by an address from a specific collection. This returns the count of NFTs, not individual token IDs. |
| get_erc1155_balance | Get the balance of a specific ERC1155 token ID owned by an address. ERC1155 allows multiple tokens of the same ID, so the balance can be greater than 1. |


## 检查服务 ## Inspector

工具在线测试： [https://mcp.xiaobenyang.com/inspector/1777316659581955](https://mcp.xiaobenyang.com/inspector/1777316659581955)

Online Tool test [https://mcp.xiaobenyang.com/inspector/1777316659581955](https://mcp.xiaobenyang.com/inspector/1777316659581955)

## 服务配置 MCP Server Config


> #### 如何获取 XBY-APIKEY ？ How to get XBY-APIKEY ?
> 访问小笨羊科技网站 [https://xiaobenyang.com](https://xiaobenyang.com)，注册用户即可获得APIKEY
> Visit XiaoBenYang website [https://xiaobenyang.com](https://xiaobenyang.com), register and get the APIKEY.

### SSE
```json
{
  "mcpServers": {
    "区块链数据服务": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "sse",
      "url": "https://mcp.xiaobenyang.com/1777316659581955/sse"
    }
  }
}
```
### STREAMABLE HTTP
```json
{
  "mcpServers": {
    "区块链数据服务": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "streamable_http",
      "url": "https://mcp.xiaobenyang.com/1777316659581955/mcp"
    }
  }
}
```
### STDIO
```json
{
    "mcpServers": {
        "区块链数据服务": {
          "command": "npx",
          "args": [
            "-y",
            "xiaobenyang-mcp"
          ],
          "env": {
            "XBY_APIKEY": "<YOUR_XBY_APIKEY>",
            "mcpId": "1777316659581955",
          },
          "transport": "stdio"
        }
      }
}

```
