# Aspose Storage Cloud - shared MCP tool library

This is **not** a standalone MCP server you connect to directly - there's no real Aspose Cloud API
route for storage on its own. This is the shared core library (`aspose-storage-core-mcp`) that every
other Aspose Cloud MCP server in the [aspose-cloud](https://github.com/aspose-cloud) org depends on
and bundles, giving each of them upload/download/list/delete tools against Aspose Cloud Storage.

**Why no standalone server:** live-tested against Aspose Cloud's real `v4.0` API, there is no
product-independent storage route - `PUT/GET https://api.aspose.cloud/v4.0/storage/...` returns a
real error, and storage is only reachable nested under a real product's own gateway
(`/v4.0/words/storage/...`, `/v4.0/cells/storage/...`, etc.). Every one of this org's other MCP
servers already bundles these same 4 tools, scoped to its own product's gateway - connect to any of
them (e.g. [`aspose-words-cloud-python-mcp`](https://github.com/aspose-cloud/aspose-words-cloud-python-mcp))
to actually use these tools live.

---

## What's in this package

| Tool | What it does | Read-only | Dry-run |
|---|---|---|---|
| `storage_upload_file` | Upload a file to Aspose Cloud Storage | no | yes |
| `storage_download_file` | Download a file from Aspose Cloud Storage | yes | - |
| `storage_list_files` | List files in an Aspose Cloud Storage folder | yes | - |
| `storage_delete_file` | Delete a file from Aspose Cloud Storage | no | yes |

These 4 functions take a `product: str` parameter identifying which product's gateway to call
through - every bundling server binds this internally; it is never an agent-facing tool parameter.

---

## License

MIT (see [`LICENSE`](LICENSE)) — covers only this repository's own MCP wrapper/integration code.
It does **not** cover, and grants no rights to, the Aspose Cloud product or API themselves, which
remain governed entirely by [Aspose's own product and usage terms](https://purchase.aspose.cloud/policies).
A valid Aspose Cloud account and subscription/credentials are required to actually call the API,
regardless of this code's license.
