# Reference
<details><summary><code>client.<a href="src/runcaptain/client.py">post_v2collections_collection_name_documents_wipe</a>(...) -&gt; AsyncHttpResponse[None]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.post_v2collections_collection_name_documents_wipe(
    collection_name="collection_name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.<a href="src/runcaptain/client.py">post_v2datasets_search</a>() -&gt; AsyncHttpResponse[None]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.post_v2datasets_search()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Collections
<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">list_collections_v2</a>() -&gt; AsyncHttpResponse[CollectionListResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all collections for an organization.

Returns an array of collection objects with collection_name, collection_id, and document_count.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.list_collections_v2()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">create_collection_v2</a>(...) -&gt; AsyncHttpResponse[CollectionResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a new collection (idempotent). Returns 201 if created, 200 if already exists.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.create_collection_v2(
    collection_name="collection_name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">delete_collection_v2</a>(...) -&gt; AsyncHttpResponse[StandardResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a collection and all its indexed documents.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.delete_collection_v2(
    collection_name="collection_name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">change_collection_environment_v2</a>(...) -&gt; AsyncHttpResponse[ChangeEnvironmentResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Move a collection from one environment to another (e.g., development to production) without reindexing.

All files, indexed data, and vector embeddings are preserved. The collection's internal ID stays the same — only the environment label changes.

## Use Cases
- Promote a development collection to production after testing
- Move a production collection back to staging for debugging
- Reorganize collections across environments

## Error Cases
- **400**: Collection is already in the target environment
- **404**: Collection not found in current environment
- **409**: A collection with the same name already exists in the target environment
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.change_collection_environment_v2(
    collection_name="collection_name",
    new_environment="development",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**new_environment:** `ChangeEnvironmentRequestV2NewEnvironment` — The target environment to move the collection to
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">list_documents_v2</a>(...) -&gt; AsyncHttpResponse[DocumentListResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all documents in a collection with pagination support.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.list_documents_v2(
    collection_name="collection_name",
    offset=1,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**offset:** `typing.Optional[int]` — Pagination offset
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">wipe_collection_documents_v2</a>(...) -&gt; AsyncHttpResponse[DocumentDeleteResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Remove all documents from a collection while keeping the collection structure.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.wipe_collection_documents_v2(
    collection_name="collection_name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` — Name of the collection to wipe
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">delete_document_v2</a>(...) -&gt; AsyncHttpResponse[StandardResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a specific document from a collection.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.collections.delete_document_v2(
    collection_name="collection_name",
    document_id="document_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Query
<details><summary><code>client.query.<a href="src/runcaptain/query/client.py">collection_v2</a>(...) -&gt; AsyncHttpResponse[QueryResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Execute a natural language query against a collection.

When `inference=true`, returns an AI-generated response with relevant documents.
When `inference=false`, returns raw search results with content and metadata.

## Streaming (SSE)

When `stream: true` and `inference: true`, the JSON response includes a `request_id`. Refer to the sample implementations to best make use of streams.

### SSE Event Types

| Event | Format | Description |
|-------|--------|-------------|
| Text chunk | `data: <text>\n\n` | Incremental text of the AI response. Plain text (not JSON). Newlines within text are escaped as `\n`. |
| Tool start | `event: tool_start\ndata: {"type":"tool.start","name":"searchKnowledgeBase","tool_call_id":"tc_1","args":{"query":"..."}}\n\n` | The AI agent is performing a knowledge base search. The `args.query` field contains the search query. |
| Tool end | `event: tool_end\ndata: {"type":"tool.end","name":"searchKnowledgeBase","tool_call_id":"tc_1","ok":true,"result_summary":{"resultCount":12}}\n\n` | A search completed. `tool_call_id` correlates with the preceding `tool_start`. `result_summary.resultCount` indicates how many results were found. |
| Complete | `event: complete\ndata: {"type":"stream_complete"}\n\n` | Stream finished successfully. Close the connection after receiving this. |
| Error | `event: error\ndata: {"type":"stream_error","error":"..."}\n\n` | An error occurred during generation. Close the connection. |

### Example SSE Stream

```
event: tool_start
data: {"type":"tool.start","name":"searchKnowledgeBase","tool_call_id":"tc_1","args":{"query":"revenue projections Q4"}}

event: tool_end
data: {"type":"tool.end","name":"searchKnowledgeBase","tool_call_id":"tc_1","ok":true,"result_summary":{"resultCount":12}}

data: Based on the documents
data:  provided, the revenue
data:  projections for Q4 show
data:  a 15% increase over Q3.

event: tool_start
data: {"type":"tool.start","name":"searchKnowledgeBase","tool_call_id":"tc_2","args":{"query":"Q3 comparison metrics"}}

event: tool_end
data: {"type":"tool.end","name":"searchKnowledgeBase","tool_call_id":"tc_2","ok":true,"result_summary":{"resultCount":8}}

data:  Compared to Q3, the key
data:  drivers were operational
data:  efficiency gains.

event: complete
data: {"type":"stream_complete"}
```

### Notes

- The agent may perform multiple searches per query. Each search produces a `tool_start`/`tool_end` pair.
- Text chunks are interleaved between tool events — text arrives after the agent has gathered results from a search.
- Connect with `Accept: text/event-stream` and set a generous timeout (120s+) for long responses.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.query.collection_v2(
    collection_name="collection_name",
    query="Find Q3 contracts mentioning 'termination for convenience'",
    inference=True,
    stream=False,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**query:** `str` — The natural language query to search for
    
</dd>
</dl>

<dl>
<dd>

**inference:** `typing.Optional[bool]` — Enable LLM-generated answers based on the relevant sections retrieved. When false, returns raw search results.
    
</dd>
</dl>

<dl>
<dd>

**stream:** `typing.Optional[bool]` — Enable real-time streaming of the response
    
</dd>
</dl>

<dl>
<dd>

**top_k:** `typing.Optional[int]` — Number of results to return. Only valid when inference=false. Not supported when inference=true (the agent controls its own search strategy).
    
</dd>
</dl>

<dl>
<dd>

**rerank:** `typing.Optional[bool]` — Enable Voyage AI rerank-2.5 reranking for improved relevance ordering. Adds ~100-300ms latency.
    
</dd>
</dl>

<dl>
<dd>

**metadata_filter:** `typing.Optional[typing.Dict[str, typing.Any]]` — Filter expression for vector search. Supports: $eq, $ne, $gt, $gte, $lt, $lte, $in, $nin, $and, $or
    
</dd>
</dl>

<dl>
<dd>

**custom_prompt:** `typing.Optional[str]` — Custom system prompt to override the default RAG prompt when inference=true. Allows customizing how the LLM processes and responds to the query with the retrieved context.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Indexing
<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_s3bucket_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from an S3 bucket into a collection. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_s3bucket_v2(
    collection_name="collection_name",
    bucket_name="my-company-docs",
    aws_access_key_id="AKIAIOSFODNN7EXAMPLE",
    aws_secret_access_key="wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
    bucket_region="us-east-1",
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**bucket_name:** `str` — Name of the S3 bucket
    
</dd>
</dl>

<dl>
<dd>

**aws_access_key_id:** `str` — AWS access key ID with read access to the bucket
    
</dd>
</dl>

<dl>
<dd>

**aws_secret_access_key:** `str` — AWS secret access key
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexS3RequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**bucket_region:** `typing.Optional[str]` — AWS region where the bucket is located
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — Maximum number of files to index (optional)
    
</dd>
</dl>

<dl>
<dd>

**skip_existing:** `typing.Optional[bool]` — Skip files that are already indexed in the collection. When true, only new files will be indexed. Set to false to re-index all files.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_s3file_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index a single file from an S3 bucket into a collection. Returns a job_id for tracking progress.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_s3file_v2(
    collection_name="collection_name",
    bucket_name="my-company-docs",
    file_uri="s3://my-company-docs/contracts/acme_contract.pdf",
    aws_access_key_id="AKIAIOSFODNN7EXAMPLE",
    aws_secret_access_key="wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
    bucket_region="us-east-1",
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**bucket_name:** `str` — Name of the S3 bucket
    
</dd>
</dl>

<dl>
<dd>

**file_uri:** `str` — S3 URI format: s3://bucket-name/path/to/file.pdf
    
</dd>
</dl>

<dl>
<dd>

**aws_access_key_id:** `str` — AWS access key ID with read access to the bucket
    
</dd>
</dl>

<dl>
<dd>

**aws_secret_access_key:** `str` — AWS secret access key
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexS3FileRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**bucket_region:** `typing.Optional[str]` — AWS region where the bucket is located
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all chunks from this file. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_gcs_bucket_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a Google Cloud Storage bucket into a collection. Returns a job_id for tracking progress.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_gcs_bucket_v2(
    collection_name="collection_name",
    bucket_name="my-company-docs",
    service_account_json='{"type":"service_account","project_id":"my-project",...}',
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**bucket_name:** `str` — Name of the GCS bucket
    
</dd>
</dl>

<dl>
<dd>

**service_account_json:** `str` — GCP service account JSON key with read access to the bucket
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexGcsRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — Maximum number of files to index (optional)
    
</dd>
</dl>

<dl>
<dd>

**skip_existing:** `typing.Optional[bool]` — Skip files that are already indexed in the collection. When true, only new files will be indexed. Set to false to re-index all files.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_gcs_file_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index a single file from a GCS bucket into a collection. Returns a job_id for tracking progress.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_gcs_file_v2(
    collection_name="collection_name",
    bucket_name="my-company-docs",
    file_uri="gs://my-company-docs/contracts/acme_contract.pdf",
    service_account_json='{"type":"service_account","project_id":"my-project",...}',
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**bucket_name:** `str` — Name of the GCS bucket
    
</dd>
</dl>

<dl>
<dd>

**file_uri:** `str` — GCS URI format: gs://bucket-name/path/to/file.pdf
    
</dd>
</dl>

<dl>
<dd>

**service_account_json:** `str` — GCP service account JSON key with read access to the bucket
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexGcsFileRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all chunks from this file. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_s3directory_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a specific directory in an S3 bucket into a collection. Uses prefix-based filtering to index only files within the specified directory path. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_s3directory_v2(
    collection_name="collection_name",
    bucket_name="my-company-docs",
    directory_path="reports/2024/january",
    aws_access_key_id="AKIAIOSFODNN7EXAMPLE",
    aws_secret_access_key="wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
    bucket_region="us-east-1",
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**bucket_name:** `str` — Name of the S3 bucket
    
</dd>
</dl>

<dl>
<dd>

**directory_path:** `str` — Path to the directory within the bucket. Accepts either a relative path (e.g., 'reports/2024/january') or a full S3 URI (e.g., 's3://my-bucket/reports/2024/january'). All files within this directory and its subdirectories will be indexed.
    
</dd>
</dl>

<dl>
<dd>

**aws_access_key_id:** `str` — AWS access key ID with read access to the bucket
    
</dd>
</dl>

<dl>
<dd>

**aws_secret_access_key:** `str` — AWS secret access key
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexS3DirectoryRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**bucket_region:** `typing.Optional[str]` — AWS region where the bucket is located
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — Maximum number of files to index (optional)
    
</dd>
</dl>

<dl>
<dd>

**skip_existing:** `typing.Optional[bool]` — Skip files that are already indexed in the collection. When true, only new files will be indexed. Set to false to re-index all files.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_gcs_directory_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a specific directory in a GCS bucket into a collection. Uses prefix-based filtering to index only files within the specified directory path. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_gcs_directory_v2(
    collection_name="collection_name",
    bucket_name="my-company-docs",
    directory_path="reports/2024/january",
    service_account_json='{"type":"service_account","project_id":"my-project",...}',
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**bucket_name:** `str` — Name of the GCS bucket
    
</dd>
</dl>

<dl>
<dd>

**directory_path:** `str` — Path to the directory within the bucket. Accepts either a relative path (e.g., 'reports/2024/january') or a full GCS URI (e.g., 'gs://my-bucket/reports/2024/january'). All files within this directory and its subdirectories will be indexed.
    
</dd>
</dl>

<dl>
<dd>

**service_account_json:** `str` — GCP service account JSON key with read access to the bucket
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexGcsDirectoryRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — Maximum number of files to index (optional)
    
</dd>
</dl>

<dl>
<dd>

**skip_existing:** `typing.Optional[bool]` — Skip files that are already indexed in the collection. When true, only new files will be indexed. Set to false to re-index all files.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_azure_container_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from an Azure Blob Storage container into a collection. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_azure_container_v2(
    collection_name="collection_name",
    container_name="my-container",
    account_name="mystorageaccount",
    account_key="your_account_key_base64",
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**container_name:** `str` — Name of the Azure Blob Storage container
    
</dd>
</dl>

<dl>
<dd>

**account_name:** `str` — Azure Storage account name
    
</dd>
</dl>

<dl>
<dd>

**account_key:** `str` — Azure Storage account key (base64-encoded)
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexAzureRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — Maximum number of files to index (optional)
    
</dd>
</dl>

<dl>
<dd>

**skip_existing:** `typing.Optional[bool]` — Skip files that are already indexed in the collection. When true, only new files will be indexed. Set to false to re-index all files.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_azure_file_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index a single file from an Azure Blob Storage container into a collection. Returns a job_id for tracking progress.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_azure_file_v2(
    collection_name="collection_name",
    container_name="my-container",
    file_uri="https://mystorageaccount.blob.core.windows.net/my-container/contracts/acme_contract.pdf",
    account_name="mystorageaccount",
    account_key="your_account_key_base64",
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**container_name:** `str` — Name of the Azure Blob Storage container
    
</dd>
</dl>

<dl>
<dd>

**file_uri:** `str` — Azure Blob Storage URI format: https://{account}.blob.core.windows.net/{container}/path/to/file.pdf
    
</dd>
</dl>

<dl>
<dd>

**account_name:** `str` — Azure Storage account name
    
</dd>
</dl>

<dl>
<dd>

**account_key:** `str` — Azure Storage account key (base64-encoded)
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexAzureFileRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all chunks from this file. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_azure_directory_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a specific directory (prefix) in an Azure Blob Storage container into a collection. Uses prefix-based filtering to index only blobs within the specified path. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.indexing.index_azure_directory_v2(
    collection_name="collection_name",
    container_name="my-container",
    directory_path="reports/2024/january",
    account_name="mystorageaccount",
    account_key="your_account_key_base64",
    processing_type="advanced",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**collection_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**container_name:** `str` — Name of the Azure Blob Storage container
    
</dd>
</dl>

<dl>
<dd>

**directory_path:** `str` — Path to the directory (prefix) within the container. Accepts either a relative path (e.g., 'reports/2024/january') or a full Azure Blob URI (e.g., 'https://account.blob.core.windows.net/container/reports/2024/january'). All blobs within this prefix will be indexed.
    
</dd>
</dl>

<dl>
<dd>

**account_name:** `str` — Azure Storage account name
    
</dd>
</dl>

<dl>
<dd>

**account_key:** `str` — Azure Storage account key (base64-encoded)
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexAzureDirectoryRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — Maximum number of files to index (optional)
    
</dd>
</dl>

<dl>
<dd>

**skip_existing:** `typing.Optional[bool]` — Skip files that are already indexed in the collection. When true, only new files will be indexed. Set to false to re-index all files.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Jobs
<details><summary><code>client.jobs.<a href="src/runcaptain/jobs/client.py">get_job_status_v2</a>(...) -&gt; AsyncHttpResponse[JobStatusResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the status of an indexing job with detailed progress information.

## Status Values
- **pending**: Job created but processing hasn't started yet
- **running**: Job is actively processing files
- **completed**: Job finished successfully
- **failed**: Job encountered an error
- **cancelled**: Job was cancelled by user

## Processing Stages
When status is `running`, the `progress.current_stage` field indicates which stage:
1. **scanning**: Scanning bucket for files
2. **extracting**: Extracting text content from documents
3. **chunking**: Splitting documents into semantic chunks
4. **tagging**: AI tagging and summarization
5. **embedding**: Generating vector embeddings
6. **finalizing**: Aggregating results and recording billing

## File Status Values
Each file in the `files` array has a status:
- **queued**: Waiting to be processed
- **processing**: Currently being processed
- **completed**: Successfully indexed
- **failed**: Failed to process (see error_code/error_message)
- **skipped**: Skipped (already indexed, unsupported type, etc.)
- **cancelled**: Processing was cancelled
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.jobs.get_job_status_v2(
    job_id="job_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**job_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/runcaptain/jobs/client.py">cancel_job_v2</a>(...) -&gt; AsyncHttpResponse[JobCancelResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel an indexing job.

Behavior:
- If job is pending or running -> transitions to cancelled
- If job is already completed/failed/cancelled -> returns 200 with current state (idempotent)
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.jobs.cancel_job_v2(
    job_id="job_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**job_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Datasets
<details><summary><code>client.datasets.<a href="src/runcaptain/datasets/client.py">search_dataset</a>(...) -&gt; AsyncHttpResponse[DatasetSearchResponse]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for articles within a news dataset.

Uses Google Search constrained to the dataset's domain to find relevant articles.

## Supported Datasets
- **nytimes**: New York Times (nytimes.com)
- **washpost**: Washington Post (washingtonpost.com)
- **sfstandard**: SF Standard (sfstandard.com)

## Response
Returns a list of search results with title, URL, snippet, and date.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.datasets.search_dataset(
    dataset="nytimes",
    q="q",
    limit=1,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset:** `SearchDatasetRequestDataset` — The news dataset to search. Supported: nytimes, washpost, sfstandard
    
</dd>
</dl>

<dl>
<dd>

**q:** `str` — Search query
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (default: 10, max: 100)
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/runcaptain/datasets/client.py">get_dataset_article</a>(...) -&gt; AsyncHttpResponse[DatasetArticleResponse]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a full article from a supported news dataset.

## Supported Datasets
- **nytimes**: New York Times (nytimes.com)
- **washpost**: Washington Post (washingtonpost.com)
- **sfstandard**: SF Standard (sfstandard.com)

## URL Path
The article URL is appended directly to the endpoint path. The URL must match the domain of the specified dataset.

## Response
Returns the full article content in markdown format, along with metadata like title, author, date, and character count.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from runcaptain import Captain

client = Captain(
    organization_id="YOUR_ORGANIZATION_ID",
    key="YOUR_KEY",
)
client.datasets.get_dataset_article(
    dataset="nytimes",
    url="url",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset:** `GetDatasetArticleRequestDataset` — The news dataset to get articles from. Supported: nytimes, washpost, sfstandard
    
</dd>
</dl>

<dl>
<dd>

**url:** `str` — Full URL of the article to get, appended to the path. Must match the dataset's domain.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

