# Reference
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
    collection_name="my_documents",
    description="A collection of research documents",
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
    collection_name="my_documents",
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

All files, indexed data, and vector embeddings are preserved. The collection's internal ID stays the same â€” only the environment label changes.

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
    collection_name="my_documents",
    new_environment="production",
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
    collection_name="my_documents",
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
    collection_name="my_documents",
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
    collection_name="my_documents",
    document_id="doc_abc123",
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
<details><summary><code>client.query.<a href="src/runcaptain/query/client.py">collection_v2stream</a>(...) -&gt; typing.AsyncIterator[AsyncHttpResponse[typing.AsyncIterator[QueryStreamEvent]]]</code></summary>
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

When `stream: true` and `inference: true`, the response is a Server-Sent Events stream. Every `data:` field is a JSON object with a `type` discriminator.

### SSE Event Types

| `type` value | Schema | Description |
|---|---|---|
| `text.delta` | `QueryStreamTextEvent` | Incremental text chunk of the AI response. |
| `tool.start` | `QueryStreamToolStartEvent` | The agent is performing a knowledge-base search. |
| `tool.end` | `QueryStreamToolEndEvent` | A tool call completed. `tool_call_id` correlates with the preceding `tool.start`. |
| `stream_complete` | `QueryStreamCompleteEvent` | Stream finished successfully. Close the connection. |
| `stream_error` | `QueryStreamErrorEvent` | An error occurred. Close the connection. |

### Example SSE Stream

```
data: {"type":"tool.start","seq":1,"run_id":"run_abc","tool_call_id":"tc_1","name":"searchKnowledgeBase","args":{"query":"revenue projections Q4"}}

data: {"type":"tool.end","seq":2,"run_id":"run_abc","tool_call_id":"tc_1","name":"searchKnowledgeBase","ok":true,"result_summary":{"resultCount":12}}

data: {"type":"text.delta","seq":3,"run_id":"run_abc","data":"Based on the documents"}
data: {"type":"text.delta","seq":4,"run_id":"run_abc","data":" provided, the revenue"}
data: {"type":"text.delta","seq":5,"run_id":"run_abc","data":" projections for Q4 show"}
data: {"type":"text.delta","seq":6,"run_id":"run_abc","data":" a 15% increase over Q3."}

data: {"type":"stream_complete","metadata":{"totalResults":12,"totalSearches":1},"stats":{"totalTokens":150}}
```

### Notes

- The agent may perform multiple searches per query. Each search produces a `tool.start` / `tool.end` pair.
- Text chunks are interleaved between tool events â€” text arrives after the agent has gathered results from a search.
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
response = client.query.collection_v2stream(
    collection_name="collection_name",
    query="query",
)
for chunk in response.data:
    yield chunk

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

When `stream: true` and `inference: true`, the response is a Server-Sent Events stream. Every `data:` field is a JSON object with a `type` discriminator.

### SSE Event Types

| `type` value | Schema | Description |
|---|---|---|
| `text.delta` | `QueryStreamTextEvent` | Incremental text chunk of the AI response. |
| `tool.start` | `QueryStreamToolStartEvent` | The agent is performing a knowledge-base search. |
| `tool.end` | `QueryStreamToolEndEvent` | A tool call completed. `tool_call_id` correlates with the preceding `tool.start`. |
| `stream_complete` | `QueryStreamCompleteEvent` | Stream finished successfully. Close the connection. |
| `stream_error` | `QueryStreamErrorEvent` | An error occurred. Close the connection. |

### Example SSE Stream

```
data: {"type":"tool.start","seq":1,"run_id":"run_abc","tool_call_id":"tc_1","name":"searchKnowledgeBase","args":{"query":"revenue projections Q4"}}

data: {"type":"tool.end","seq":2,"run_id":"run_abc","tool_call_id":"tc_1","name":"searchKnowledgeBase","ok":true,"result_summary":{"resultCount":12}}

data: {"type":"text.delta","seq":3,"run_id":"run_abc","data":"Based on the documents"}
data: {"type":"text.delta","seq":4,"run_id":"run_abc","data":" provided, the revenue"}
data: {"type":"text.delta","seq":5,"run_id":"run_abc","data":" projections for Q4 show"}
data: {"type":"text.delta","seq":6,"run_id":"run_abc","data":" a 15% increase over Q3."}

data: {"type":"stream_complete","metadata":{"totalResults":12,"totalSearches":1},"stats":{"totalTokens":150}}
```

### Notes

- The agent may perform multiple searches per query. Each search produces a `tool.start` / `tool.end` pair.
- Text chunks are interleaved between tool events â€” text arrives after the agent has gathered results from a search.
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
    collection_name="my_documents",
    query="What are the key terms in the contract?",
    inference=True,
    rerank=True,
    top_k=10,
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
    collection_name="my_documents",
    bucket_name="my-documents-bucket",
    aws_access_key_id="AKIAIOSFODNN7EXAMPLE",
    aws_secret_access_key="wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
    bucket_region="us-east-1",
    processing_type="advanced",
    skip_existing=True,
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
    collection_name="my_documents",
    bucket_name="my-documents-bucket",
    file_uri="s3://my-documents-bucket/reports/quarterly-report-q4.pdf",
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
    collection_name="my_documents",
    bucket_name="my-gcs-documents",
    service_account_json='{"type": "service_account", "project_id": "my-project", ...}',
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
    collection_name="my_documents",
    bucket_name="my-gcs-documents",
    file_uri="gs://my-gcs-documents/reports/annual-review.pdf",
    service_account_json='{"type": "service_account", "project_id": "my-project", ...}',
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
    collection_name="my_documents",
    bucket_name="my-documents-bucket",
    directory_path="reports/2025/",
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
    collection_name="my_documents",
    bucket_name="my-gcs-documents",
    directory_path="reports/2025/",
    service_account_json='{"type": "service_account", "project_id": "my-project", ...}',
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
    collection_name="my_documents",
    container_name="my-azure-documents",
    account_name="mystorageaccount",
    account_key="base64encodedaccountkey==",
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
    collection_name="my_documents",
    container_name="my-azure-documents",
    file_uri="https://mystorageaccount.blob.core.windows.net/my-azure-documents/reports/annual-review.pdf",
    account_name="mystorageaccount",
    account_key="base64encodedaccountkey==",
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
    collection_name="my_documents",
    container_name="my-azure-documents",
    directory_path="reports/2025/",
    account_name="mystorageaccount",
    account_key="base64encodedaccountkey==",
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_r2bucket_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a Cloudflare R2 bucket into a collection. R2 is S3-compatible â€” provide your R2 API token's Access Key ID and Secret Access Key. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
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
client.indexing.index_r2bucket_v2(
    collection_name="my_documents",
    bucket_name="my-r2-bucket",
    account_id="your_cloudflare_account_id",
    access_key_id="your_r2_access_key_id",
    secret_access_key="your_r2_secret_access_key",
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

**bucket_name:** `str` — Name of the R2 bucket
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `str` — Cloudflare account ID (found in your R2 dashboard URL)
    
</dd>
</dl>

<dl>
<dd>

**access_key_id:** `str` — R2 S3 API token Access Key ID
    
</dd>
</dl>

<dl>
<dd>

**secret_access_key:** `str` — R2 S3 API token Secret Access Key
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexR2RequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**jurisdiction:** `typing.Optional[IndexR2RequestV2Jurisdiction]` — R2 jurisdiction. 'default' for global, 'eu' for EU-only storage, 'fedramp' for FedRAMP-compliant storage.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_r2file_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index a single file from a Cloudflare R2 bucket into a collection. Returns a job_id for tracking progress.
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
client.indexing.index_r2file_v2(
    collection_name="my_documents",
    bucket_name="my-r2-bucket",
    file_uri="r2://my-r2-bucket/reports/annual-review.pdf",
    account_id="your_cloudflare_account_id",
    access_key_id="your_r2_access_key_id",
    secret_access_key="your_r2_secret_access_key",
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

**bucket_name:** `str` — Name of the R2 bucket
    
</dd>
</dl>

<dl>
<dd>

**file_uri:** `str` — R2 URI format: r2://bucket-name/path/to/file.pdf
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `str` — Cloudflare account ID (found in your R2 dashboard URL)
    
</dd>
</dl>

<dl>
<dd>

**access_key_id:** `str` — R2 S3 API token Access Key ID
    
</dd>
</dl>

<dl>
<dd>

**secret_access_key:** `str` — R2 S3 API token Secret Access Key
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexR2FileRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**jurisdiction:** `typing.Optional[IndexR2FileRequestV2Jurisdiction]` — R2 jurisdiction. 'default' for global, 'eu' for EU-only storage, 'fedramp' for FedRAMP-compliant storage.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_r2directory_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a specific directory (prefix) in a Cloudflare R2 bucket into a collection. Uses prefix-based filtering to index only objects within the specified path. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
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
client.indexing.index_r2directory_v2(
    collection_name="my_documents",
    bucket_name="my-r2-bucket",
    directory_path="reports/2025/",
    account_id="your_cloudflare_account_id",
    access_key_id="your_r2_access_key_id",
    secret_access_key="your_r2_secret_access_key",
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

**bucket_name:** `str` — Name of the R2 bucket
    
</dd>
</dl>

<dl>
<dd>

**directory_path:** `str` — Path to the directory (prefix) within the bucket. Accepts either a relative path (e.g., 'reports/2024/january') or a full R2 URI (e.g., 'r2://my-bucket/reports/2024/january'). All objects within this prefix will be indexed.
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `str` — Cloudflare account ID (found in your R2 dashboard URL)
    
</dd>
</dl>

<dl>
<dd>

**access_key_id:** `str` — R2 S3 API token Access Key ID
    
</dd>
</dl>

<dl>
<dd>

**secret_access_key:** `str` — R2 S3 API token Secret Access Key
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexR2DirectoryRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**jurisdiction:** `typing.Optional[IndexR2DirectoryRequestV2Jurisdiction]` — R2 jurisdiction. 'default' for global, 'eu' for EU-only storage, 'fedramp' for FedRAMP-compliant storage.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_url_v2</a>(...) -&gt; AsyncHttpResponse[IndexJobResponseV2]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index documents from public URLs into a collection. No cloud storage credentials required.

You can provide either:
- `url` â€” a single URL string for one document
- `urls` â€” an array of URL strings for multiple documents

Supported file types: PDF, DOCX, DOC, XLSX, XLS, CSV, TSV, TXT, MD, JSON, YAML, YML, PNG, JPG, JPEG, GIF, BMP, TIFF. Documents are downloaded and processed through the same pipeline as cloud storage indexing.

Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
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
client.indexing.index_url_v2(
    collection_name="my_documents",
    urls=[
        "https://example.com/documents/report.pdf",
        "https://example.com/documents/memo.txt",
        "https://example.com/documents/data.csv",
    ],
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

**processing_type:** `IndexUrlRequestV2ProcessingType` — Document processing type. 'advanced' uses agentic OCR with AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images. 'basic' provides reliable OCR optimized for general document indexing and high-volume processing.
    
</dd>
</dl>

<dl>
<dd>

**url:** `typing.Optional[str]` — A single public URL to a hosted document. Supported types: PDF, DOCX, DOC, XLSX, XLS, CSV, TSV, TXT, MD, JSON, YAML, YML, PNG, JPG, JPEG, GIF, BMP, TIFF. Provide either 'url' or 'urls', not both.
    
</dd>
</dl>

<dl>
<dd>

**urls:** `typing.Optional[typing.Sequence[str]]` — An array of public URLs to hosted documents. Provide either 'url' or 'urls', not both.
    
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
    job_id="job_s3_abc123",
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
    job_id="job_s3_abc123",
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

Contact your Account Executive for available datasets.

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
    dataset="dataset_name",
    q="climate change policy",
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

**dataset:** `typing.Optional[str]` — The dataset to search. Contact your Account Executive for available datasets.
    
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

Contact your Account Executive for available datasets.

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
    dataset="dataset_name",
    url="https://www.example.com/2025/01/15/politics/example-article",
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

**dataset:** `typing.Optional[str]` — The dataset to get articles from. Contact your Account Executive for available datasets.
    
</dd>
</dl>

<dl>
<dd>

**url:** `str` 
    
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

## General
<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search across all entity types (companies, people, investors, funds, deals, etc.) in a unified query. Returns matching entities with their type and basic information. Use this for broad discovery before drilling into specific entity types.
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
client.general.search()

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

**limit:** `typing.Optional[int]` — Maximum results
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">search_shared</a>() -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for entities shared across your organization. Returns entities that multiple team members have accessed or tagged. Useful for discovering commonly referenced companies, investors, or people within your team.
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
client.general.search_shared()

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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_people</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get people associated with any entity (company employees, fund team members, investor partners, etc.). Returns names, titles, and LinkedIn profiles for key people.
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
client.general.entity_people(
    entity_id="openai",
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

**entity_id:** `str` 
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_locations</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get office locations for any entity. Returns headquarters and branch office addresses with city, state, country, and full address details.
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
client.general.entity_locations(
    entity_id="openai",
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

**entity_id:** `str` 
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_affiliates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get affiliated entities and subsidiaries for any entity. Returns parent companies, subsidiaries, and related entities with ownership information.
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
client.general.entity_affiliates(
    entity_id="openai",
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

**entity_id:** `str` 
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_news</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get recent news articles and mentions for any entity. Returns article titles, URLs, sources, publication dates, and snippets. Useful for tracking announcements, funding news, and company updates.
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
client.general.entity_news(
    entity_id="openai",
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

**entity_id:** `str` 
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of data updates for any entity. Returns history of changes to the entity's profile, tracking when information was added or modified. Useful for monitoring data freshness.
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
client.general.entity_updates(
    entity_id="openai",
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

**entity_id:** `str` 
    
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

## Companies
<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">search</a>() -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for companies by name, industry, or location. Returns matching company profiles with employee count, industry classification, founding date, and headquarters. Use this to find company entity IDs for detailed lookups.
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
client.companies.search()

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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">bio</a>(...) -&gt; AsyncHttpResponse[typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive company profile including description, founding date, headquarters location, employee count, industry classification, and social media profiles. This is the primary endpoint for company overview data.
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
client.companies.bio(
    company_id="019cb8ac-adee-749e-a75e-a1c236f20f72",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">industries</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get industry classifications including NAICS codes, SIC codes, and industry descriptions. Useful for filtering companies by vertical or sector.
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
client.companies.industries(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">financials</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get financial statements for public companies including revenue, net income, assets, and liabilities. Returns most recent fiscal year data or specific year if requested.
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
client.companies.financials(
    company_id="ody_co_sample_msft",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">financials_recent</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get most recent financial statements for public companies. Convenience endpoint that automatically returns the latest available fiscal year data.
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
client.companies.financials_recent(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">financing_recent</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get most recent funding rounds including round type, amount raised, investors, and valuation. Returns detailed information about the latest equity financing event.
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
client.companies.financing_recent(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">active_investors</a>(...) -&gt; AsyncHttpResponse[typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get current investors in the company from recent funding rounds. Returns investor names, types, and contact information.
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
client.companies.active_investors(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">all_investors</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get complete investor history including historical investors from all funding rounds. Returns comprehensive list of all investors who have participated in company financing.
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
client.companies.all_investors(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">deals</a>(...) -&gt; AsyncHttpResponse[typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get all deals for a company including funding rounds and acquisitions. Each deal includes the deal type, round name, investors involved, amount raised, and status. Funding rounds are sourced from investor data, while acquisitions are sourced from M&A records.
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
client.companies.deals(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">service_providers</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get service providers working with the company including legal counsel, accounting firms, and consultants. Returns firm names, service types, and engagement information.
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
client.companies.service_providers(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">service_providers_deal</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get service providers involved in specific financing deals including investment bankers, legal advisors, and financial consultants. Returns provider details specific to fundraising transactions.
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
client.companies.service_providers_deal(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">debt_financing_recent</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get most recent debt financing rounds including venture debt, credit lines, and loans. Returns lender information, amounts, and terms.
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
client.companies.debt_financing_recent(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">similar</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get companies similar to this one based on industry, size, and business model. Returns competitor and peer company information with similarity scores.
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
client.companies.similar(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">social_analytics</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get social media metrics including LinkedIn followers, Twitter engagement, and Facebook presence. Useful for measuring company online visibility and growth.
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
client.companies.social_analytics(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">vc_exit_predictions</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get predicted likelihood and timeline for company exit events (IPO or acquisition). Will return ML-based exit probability scores and estimated exit valuation ranges when implemented.
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
client.companies.vc_exit_predictions(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to company profile data. Returns history of changes to company information with timestamps and modified fields.
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
client.companies.updates(
    company_id="openai.com",
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

**company_id:** `str` 
    
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

## People
<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for professionals by name, company, title, or location. Returns matching profiles with current position, company, and LinkedIn URL. Use this to find person entity IDs for detailed lookups.
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
client.people.search()

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

**title:** `typing.Optional[str]` — Filter by job title
    
</dd>
</dl>

<dl>
<dd>

**location:** `typing.Optional[str]` — Filter by location
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum results
    
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

<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">bio</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive person profile including headline, summary, current company, location, and social profiles. This is the primary endpoint for person overview data.
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
client.people.bio(
    person_id="ody_pe_019cb8ac-f123-749e-a75e-e5f669g53c05",
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

**person_id:** `str` 
    
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

<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">contact</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get contact information including email addresses, phone numbers, and social media profiles. Returns verified contact details for outreach.
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
client.people.contact(
    person_id="linkedin.com/in/samaltman",
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

**person_id:** `str` 
    
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

<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">education_work</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get complete professional history including work experience and education. Returns job positions with companies, titles, dates, and degree information with schools and majors.
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
client.people.education_work(
    person_id="linkedin.com/in/samaltman",
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

**person_id:** `str` 
    
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

<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to person profile data. Returns history of career moves, title changes, and profile updates with timestamps.
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
client.people.updates(
    person_id="linkedin.com/in/samaltman",
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

**person_id:** `str` 
    
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

## Deals
<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for funding rounds and deals by company, deal type, amount range, or date. Returns matching transactions with deal type, amount, date, and participants. Use this to find deal entity IDs for detailed lookups.
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
client.deals.search()

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

**deal_type:** `typing.Optional[str]` — Filter by deal type
    
</dd>
</dl>

<dl>
<dd>

**min_amount:** `typing.Optional[float]` — Minimum deal amount
    
</dd>
</dl>

<dl>
<dd>

**max_amount:** `typing.Optional[float]` — Maximum deal amount
    
</dd>
</dl>

<dl>
<dd>

**start_date:** `typing.Optional[str]` — Start date (YYYY-MM-DD)
    
</dd>
</dl>

<dl>
<dd>

**end_date:** `typing.Optional[str]` — End date (YYYY-MM-DD)
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Results per page
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">bio</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive deal information including amount, type, date, company, and investor participants. This is the primary endpoint for deal overview data.
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
client.deals.bio(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">detailed</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive deal data combining bio, investors, valuation, and terms in a single response. Use this for complete deal intelligence without multiple API calls.
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
client.deals.detailed(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">investors</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get all investors participating in the deal including lead and follow-on investors. Returns investor names, roles, and investment amounts.
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
client.deals.investors(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">service_providers</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get service providers involved in the deal including legal counsel, investment bankers, and financial advisors. Returns firm names and service types.
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
client.deals.service_providers(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">valuation</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get valuation information including pre-money and post-money valuations, equity percentage, and pricing details. Useful for understanding deal economics.
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
client.deals.valuation(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">stock_info</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get current stock price and market data for the company involved in this deal. Only applicable for public companies. Returns real-time stock quotes and market metrics.
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
client.deals.stock_info(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">cap_table</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get capitalization table showing ownership breakdown after the deal. Will return equity ownership percentages, share counts, and investor stakes when implemented.
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
client.deals.cap_table(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">tranche</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get information about deal tranches and payment schedules for structured financing. Will return tranche amounts, dates, and conditions when implemented.
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
client.deals.tranche(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">debt_lenders</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get lenders participating in debt financing deals. Returns lender names, amounts, and terms for venture debt and credit facilities.
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
client.deals.debt_lenders(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">multiples</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get valuation multiples for the deal including revenue multiple, EBITDA multiple, and comparable transaction metrics. Will return detailed valuation analysis when implemented.
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
client.deals.multiples(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to deal information. Returns history of changes to deal data with timestamps and modified fields.
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
client.deals.updates(
    id="deal_openai_0",
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

**id:** `str` 
    
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

## Investors
<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for venture capital firms, angel investors, and institutional investors by name. Returns matching investor profiles with investment focus, portfolio size, and notable investments. Use this to find investor entity IDs for detailed lookups.
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
client.investors.search()

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

**page:** `typing.Optional[int]` — Page number
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Results per page
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">bio</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive investor profile including description, investment thesis, stage focus, sector focus, and notable portfolio companies. This is the primary endpoint for investor overview data.
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
client.investors.bio(
    id="ody_inv_019cb8ac-g789-749e-a75e-h7i880j64d16",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">active_investments</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get current portfolio companies that the investor has active positions in. Returns company names, investment dates, and current status.
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
client.investors.active_investments(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">all_investments</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get complete investment history including current portfolio and exited positions. Returns all companies the investor has backed with investment details and outcomes.
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
client.investors.all_investments(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">preferences</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get investment preferences including stage focus, sector preferences, geography, and typical check size. Useful for determining investment fit.
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
client.investors.preferences(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">funds</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get all funds managed by the investor including fund names, sizes, vintage years, and status. Returns complete fund portfolio for multi-fund investors.
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
client.investors.funds(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">funds_latest</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get information about the investor's most recent fund including size, vintage year, and deployment status. Useful for understanding current investment capacity.
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
client.investors.funds_latest(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">board_seats</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get board seats held by the investor's team members. Returns companies where investor partners serve on the board of directors.
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
client.investors.board_seats(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">service_providers</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get service providers used by the investor including legal counsel, fund administrators, and consultants. Returns firm names and service types.
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
client.investors.service_providers(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">service_providers_deal</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get service providers involved in the investor's deal flow including transaction advisors and due diligence firms. Returns provider details specific to deal execution.
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
client.investors.service_providers_deal(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to investor profile data. Returns history of changes including new investments, fund raises, and team changes with timestamps.
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
client.investors.updates(
    id="deal_openai_0",
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

**id:** `str` 
    
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

## Funds
<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for venture capital and private equity funds by name. Returns matching fund profiles with size, vintage year, and investment focus. Use this to find fund entity IDs for detailed lookups.
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
client.funds.search()

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

**vintage_year:** `typing.Optional[int]` — Filter by vintage year
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum results
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">bio</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive fund profile including fund size, vintage year, investment strategy, stage focus, and sector focus. This is the primary endpoint for fund overview data.
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
client.funds.bio(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">performance</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get fund performance metrics including IRR, TVPI, DPI, and RVPI. Will return LP-level performance data when implemented with proprietary fund reporting.
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
client.funds.performance(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">active_investments</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get current portfolio companies invested by this specific fund. Returns company names, investment amounts, and current status.
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
client.funds.active_investments(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">all_investments</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get complete investment history for this specific fund including current and exited positions. Returns all companies backed by the fund with outcomes.
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
client.funds.all_investments(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">commitments</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get limited partner commitments to the fund including LP names and commitment amounts. Returns investor base and capital structure.
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
client.funds.commitments(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">cash_flows</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get fund cash flow history including capital calls and distributions. Will return quarterly cash flow statements when implemented with LP reporting data.
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
client.funds.cash_flows(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">benchmark</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Coming Soon: Get fund performance compared to industry benchmarks and peer funds. Will return quartile rankings and comparative metrics when implemented.
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
client.funds.benchmark(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">people</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get investment team members for the fund including partners, principals, and associates. Returns names, titles, and LinkedIn profiles.
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
client.funds.people(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">preferences</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get investment criteria and preferences for the fund including stage focus, sector preferences, geography, and check size ranges.
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
client.funds.preferences(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to fund profile data. Returns history of changes including new investments, exits, and team changes with timestamps.
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
client.funds.updates(
    fund_id="sequoia",
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

**fund_id:** `str` 
    
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

## LimitedPartners
<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for institutional limited partners including pension funds, endowments, and family offices. Returns matching LP profiles with total commitments and fund relationships.
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
client.limited_partners.lps_search()

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

**limit:** `typing.Optional[int]` — Maximum results
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_bio</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive limited partner profile including institution type, total assets under management, investment strategy, and notable fund commitments. This is the primary endpoint for LP overview data.
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
client.limited_partners.lps_bio(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_commitments_detailed</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get detailed fund commitments including specific fund names, commitment amounts, vintage years, and commitment status. Returns complete LP portfolio.
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
client.limited_partners.lps_commitments_detailed(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_commitments_aggregates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get aggregated commitment statistics including total commitments by vintage year, fund type, and geography. Returns high-level allocation summary.
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
client.limited_partners.lps_commitments_aggregates(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_allocations_target</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get target allocation percentages by asset class, geography, and strategy. Returns investment policy guidelines and target portfolio mix.
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
client.limited_partners.lps_allocations_target(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_allocations_actual</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get actual current allocation percentages by asset class, geography, and strategy. Returns real portfolio composition and compare to targets.
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
client.limited_partners.lps_allocations_actual(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_commitment_preferences</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get commitment preferences including preferred fund sizes, vintage year focus, and investment stage preferences. Useful for GP fundraising targeting.
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
client.limited_partners.lps_commitment_preferences(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_service_providers</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get service providers used by the LP including consultants, custodians, and legal advisors. Returns firm names and service types.
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
client.limited_partners.lps_service_providers(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to LP profile data. Returns history of changes including new commitments, policy changes, and team updates with timestamps.
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
client.limited_partners.lps_updates(
    lp_id="calpers",
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

**lp_id:** `str` 
    
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

## ServiceProviders
<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for service providers including law firms, accounting firms, investment banks, and consultants. Returns matching provider profiles with specializations and notable clients.
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
client.service_providers.search()

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

**limit:** `typing.Optional[int]` — Maximum results
    
</dd>
</dl>

<dl>
<dd>

**provider_type:** `typing.Optional[str]` — Provider type filter
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">bio</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get comprehensive service provider profile including firm description, practice areas, office locations, and notable work. This is the primary endpoint for provider overview data.
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
client.service_providers.bio(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">companies</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get companies that have engaged this service provider. Returns client list with engagement types and sectors served.
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
client.service_providers.companies(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">deals</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get deals where this provider was involved as advisor, counsel, or banker. Returns transaction history with roles and deal values.
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
client.service_providers.deals(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">investors</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get investors that have engaged this service provider. Returns investor clients with engagement types and fund formation work.
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
client.service_providers.investors(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">funds</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get funds that have engaged this service provider. Returns fund formation and compliance work with engagement details.
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
client.service_providers.funds(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">limited_partners</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get limited partners that have engaged this service provider. Returns LP clients with service types and relationship details.
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
client.service_providers.limited_partners(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">updates</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get changelog of updates to service provider profile data. Returns history of changes including new engagements, office openings, and team changes with timestamps.
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
client.service_providers.updates(
    provider_id="wilson-sonsini",
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

**provider_id:** `str` 
    
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

## Patents
<details><summary><code>client.patents.<a href="src/runcaptain/patents/client.py">search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for patents by title, inventor, assignee, or classification. Returns matching patents with patent numbers, titles, filing dates, and status.
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
client.patents.search()

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

**limit:** `typing.Optional[int]` — Maximum results
    
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

<details><summary><code>client.patents.<a href="src/runcaptain/patents/client.py">get_by_id</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get detailed patent information including abstract, claims, inventors, citations, and prosecution history. Returns comprehensive patent profile.
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
client.patents.get_by_id(
    id="deal_openai_0",
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

**id:** `str` 
    
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

<details><summary><code>client.patents.<a href="src/runcaptain/patents/client.py">get_file</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Download patent file wrapper or PDF document. Returns patent documentation and prosecution history files.
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
client.patents.get_file(
    entity_id="US11234567B2",
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

**entity_id:** `str` 
    
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

## CreditAnalysis
<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_search</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for credit-related news and filings including bond issuances, credit rating changes, and default events. Returns matching news with dates, sources, and content.
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
client.credit_analysis.news_search()

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

**start_date:** `typing.Optional[str]` — Start date (YYYY-MM-DD)
    
</dd>
</dl>

<dl>
<dd>

**end_date:** `typing.Optional[str]` — End date (YYYY-MM-DD)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum results
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_recent</a>() -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get most recent credit news and filings. Returns latest credit events, ratings, and bond issuances from the past 30 days.
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
client.credit_analysis.news_recent()

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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_detail</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get detailed credit news article or filing including full text, metadata, and related entities. Returns comprehensive news item with analysis.
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
client.credit_analysis.news_detail(
    news_id="abc123def456",
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

**news_id:** `str` 
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_attachment</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Download attachment files associated with credit news including prospectuses, indentures, and rating reports. Returns document files.
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
client.credit_analysis.news_attachment(
    news_id="abc123def456",
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

**news_id:** `str` 
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_bulk</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve multiple credit news articles by ID in a single request. Returns batch results with article details for each requested ID.
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
client.credit_analysis.news_bulk(
    queries=["Apple credit rating", "Tesla debt analysis"],
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

**queries:** `typing.Optional[typing.Sequence[str]]` — List of search queries
    
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

## Fundamentals
<details><summary><code>client.fundamentals.<a href="src/runcaptain/fundamentals/client.py">sandbox</a>() -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get sample entities for testing and development. Returns mock company, person, investor, and fund data for sandbox environment testing.
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
client.fundamentals.sandbox()

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

<details><summary><code>client.fundamentals.<a href="src/runcaptain/fundamentals/client.py">lookup_tables</a>() -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get available reference lookup tables including industry codes, country codes, and entity type classifications. Returns list of available tables with descriptions.
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
client.fundamentals.lookup_tables()

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

<details><summary><code>client.fundamentals.<a href="src/runcaptain/fundamentals/client.py">lookup_table_values</a>(...) -&gt; AsyncHttpResponse[typing.Dict[str, typing.Any]]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get values from a specific lookup table. Returns table data with codes, descriptions, and hierarchical relationships for reference data.
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
client.fundamentals.lookup_table_values(
    table_id="sectors",
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

**table_id:** `str` 
    
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

