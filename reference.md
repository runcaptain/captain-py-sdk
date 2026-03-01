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
    collection_name="my_documents",
    query="What are the key terms in the contract?",
    inference=True,
    stream=True,
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

Index all files from a Cloudflare R2 bucket into a collection. R2 is S3-compatible — provide your R2 API token's Access Key ID and Secret Access Key. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
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
- `url` — a single URL string for one document
- `urls` — an array of URL strings for multiple documents

Supported file types include PDF, TXT, DOCX, CSV, XLSX, and more. Documents are downloaded and processed through the same pipeline as cloud storage indexing.

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

**url:** `typing.Optional[str]` — A single public URL to a hosted document (PDF, TXT, DOCX, etc.). Provide either 'url' or 'urls', not both.
    
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

