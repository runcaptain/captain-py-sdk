# Reference
## Collections
<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">list_collections_v2</a>(...) -> CollectionListResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**limit:** `typing.Optional[int]` — Maximum number of collections to return
    
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

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">create_collection_v2</a>(...) -> CollectionResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to create
    
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

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">delete_collection_v2</a>(...) -> StandardResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to delete
    
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

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">change_collection_environment_v2</a>(...) -> ChangeEnvironmentResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Move a collection from one environment to another (e.g., development to production) without reindexing.

All files, indexed data, and vector embeddings are preserved. The collection's internal ID stays the same  -  only the environment label changes.

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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to move
    
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

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">list_documents_v2</a>(...) -> DocumentListResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of documents to return
    
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

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">wipe_collection_documents_v2</a>(...) -> DocumentDeleteResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.collections.wipe_collection_documents_v2(
    collection_name="customer_profiles",
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

<details><summary><code>client.collections.<a href="src/runcaptain/collections/client.py">delete_document_v2</a>(...) -> StandardResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.collections.delete_document_v2(
    collection_name="customer_feedback",
    document_id="a1b2c3d4e5f678901234567890abcdef",
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

**collection_name:** `str` — Name of the collection
    
</dd>
</dl>

<dl>
<dd>

**document_id:** `str` — ID of the document to delete
    
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
<details><summary><code>client.query.<a href="src/runcaptain/query/client.py">collection_v2stream</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Execute a natural language query with server-sent streaming. Yields QueryStreamEvent union members (text.delta, tool.start, tool.end, stream_complete, stream_error) as they arrive.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.query.collection_v2stream(
    collection_name="collection_name",
    query="query",
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

**collection_name:** `str` — Name of the collection to query
    
</dd>
</dl>

<dl>
<dd>

**query:** `str` — The natural language query to search for
    
</dd>
</dl>

<dl>
<dd>

**stream:** `typing.Literal` — Enable real-time streaming of the response
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**rerank:** `typing.Optional[bool]` — Enable reranking for improved relevance ordering. Uses Gemini Flash 2.5 by default, or Voyage AI rerank-2.5 as fallback. Adds ~100-300ms latency.
    
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

**include_bbox:** `typing.Optional[bool]` — Include normalized bounding box layout data for each search result. Returns element-level positions (titles, paragraphs, tables, figures, form fields) with page coordinates for PDF and DOCX files. Only supported with inference=false.
    
</dd>
</dl>

<dl>
<dd>

**search_results:** `typing.Optional[bool]` — When inference=true, include the raw search result chunks that were used as context for the LLM response. Defaults to false. Always true when inference=false.
    
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

<details><summary><code>client.query.<a href="src/runcaptain/query/client.py">collection_v2</a>(...) -> QueryResponseV2</code></summary>
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
- Text chunks are interleaved between tool events  -  text arrives after the agent has gathered results from a search.
- Connect with `Accept: text/event-stream` and set a generous timeout (120s+) for long responses.

## Bounding Box Data

Set `include_bbox: true` (inference=false only) to receive element-level layout coordinates for each search result. Each result will include a `layout` object with normalized bounding box blocks for PDF and DOCX files.

Each block contains:
- `type`: element type (text, title, section_header, list_item, table, figure, key_value, header, footer)
- `content`: the text content
- `page`: page number
- `bbox`: normalized 0-1 coordinates `{ top, left, width, height }` relative to page dimensions
- `confidence`: extraction confidence (high/low) when available
- `image_url`: presigned URL for figure/chart images when available

Files without OCR data (TXT, CSV, images) will have `layout: null`.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.query.collection_v2stream(
    collection_name="my_documents",
    query="What are the key terms in the contract?",
    inference=True,
    rerank=True,
    top_k=10,
    include_bbox=False,
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

**collection_name:** `str` — Name of the collection to query
    
</dd>
</dl>

<dl>
<dd>

**query:** `str` — The natural language query to search for
    
</dd>
</dl>

<dl>
<dd>

**stream:** `typing.Literal` — Enable real-time streaming of the response
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**rerank:** `typing.Optional[bool]` — Enable reranking for improved relevance ordering. Uses Gemini Flash 2.5 by default, or Voyage AI rerank-2.5 as fallback. Adds ~100-300ms latency.
    
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

**include_bbox:** `typing.Optional[bool]` — Include normalized bounding box layout data for each search result. Returns element-level positions (titles, paragraphs, tables, figures, form fields) with page coordinates for PDF and DOCX files. Only supported with inference=false.
    
</dd>
</dl>

<dl>
<dd>

**search_results:** `typing.Optional[bool]` — When inference=true, include the raw search result chunks that were used as context for the LLM response. Defaults to false. Always true when inference=false.
    
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
<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_s3bucket_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_s3file_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_gcs_bucket_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_gcs_bucket_v2(
    collection_name="my_documents",
    bucket_name="my-gcs-documents",
    service_account_json="{\"type\": \"service_account\", \"project_id\": \"my-project\", ...}",
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

**collection_name:** `str` — Name of the collection to index into
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_gcs_file_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_gcs_file_v2(
    collection_name="my_documents",
    bucket_name="my-gcs-documents",
    file_uri="gs://my-gcs-documents/reports/annual-review.pdf",
    service_account_json="{\"type\": \"service_account\", \"project_id\": \"my-project\", ...}",
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

**collection_name:** `str` — Name of the collection to index into
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_s3directory_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_gcs_directory_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_gcs_directory_v2(
    collection_name="my_documents",
    bucket_name="my-gcs-documents",
    directory_path="reports/2025/",
    service_account_json="{\"type\": \"service_account\", \"project_id\": \"my-project\", ...}",
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_azure_container_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_azure_file_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_azure_directory_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_r2bucket_v2</a>(...) -> IndexJobResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index all files from a Cloudflare R2 bucket into a collection. R2 is S3-compatible  -  provide your R2 API token's Access Key ID and Secret Access Key. Returns a job_id for tracking progress via GET /v2/jobs/{job_id}.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_r2file_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_r2directory_v2</a>(...) -> IndexJobResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**collection_name:** `str` — Name of the collection to index into
    
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

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
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

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_url_v2</a>(...) -> IndexJobResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index documents or web pages from public URLs into a collection. No cloud storage credentials required.

You can provide either:
- `url`  -  a single URL string
- `urls`  -  an array of URL strings

## Smart Content Detection

The endpoint automatically detects whether a URL points to a hosted file or a web page:

- **Hosted files** (PDF, DOCX, XLSX, CSV, TXT, images, etc.) are downloaded and processed directly through the indexing pipeline.
- **Web pages** (HTML) are automatically scraped  -  text content is extracted as markdown and page images are downloaded and indexed. Bot-protected pages are handled via web unlocker technology.

## Supported Content

- **Documents**: PDF, DOCX, DOC, XLSX, XLS, CSV, TSV, TXT, MD, JSON, YAML, YML
- **Images**: PNG, JPG, JPEG, GIF, BMP, TIFF
- **Web pages**: Any public URL serving HTML  -  text and images are extracted automatically

## Processing Modes for Web Pages

- **advanced**: Extracts text content as markdown AND downloads and indexes all page images
- **basic**: Extracts text content only  -  faster and lower cost

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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_url_v2(
    collection_name="my_documents",
    url="https://example.com/documents/report.pdf",
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

**collection_name:** `str` — Name of the collection to index into
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `IndexUrlRequestV2ProcessingType` — Processing mode. For hosted documents: 'advanced' enables AI-enhanced extraction for complex layouts, tables, figures, and charts; 'basic' provides standard document processing. For web pages: 'advanced' extracts both text content and page images; 'basic' extracts text content only (faster, lower cost).
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
</dd>
</dl>

<dl>
<dd>

**url:** `typing.Optional[str]` — A single public URL to a document or web page. Hosted files (PDF, DOCX, etc.) are indexed directly. Web pages (HTML) are automatically scraped  -  text and images are extracted. Provide either 'url' or 'urls', not both.
    
</dd>
</dl>

<dl>
<dd>

**urls:** `typing.Optional[typing.List[str]]` — An array of public URLs to documents or web pages. Each URL is auto-detected  -  hosted files are indexed directly, web pages are scraped. Provide either 'url' or 'urls', not both.
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom metadata to attach to all indexed chunks. Keys must be strings. Values: str, int, float, bool, or array of strings.
    
</dd>
</dl>

<dl>
<dd>

**parsing_script:** `typing.Optional[str]` — Relative path to a JavaScript parsing script for JSON files (e.g. 'research/paper-parser'). When provided, .json files are processed through a sandboxed V8 isolate that executes the script to extract text and metadata. Without this parameter, .json files are indexed as raw text. Scripts are org-scoped and managed in the Parser Studio.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_youtube_v2</a>(...) -> IndexJobResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index YouTube video transcripts into a collection.

Fetches transcripts from YouTube videos using auto-generated or manual captions, formats them with inline timestamps, and indexes the text for semantic search.

You can provide either:
- `url`  -  a single YouTube video URL
- `urls`  -  an array of YouTube video URLs (max 20)

Transcripts are always processed as basic text (no OCR needed). Each transcript is formatted with `[HH:MM:SS]` timestamp markers so search results can reference specific moments in the video.

## Supported URL Formats
- `youtube.com/watch?v=VIDEO_ID`
- `youtu.be/VIDEO_ID`
- `youtube.com/shorts/VIDEO_ID`

## Auto-Injected Metadata
The following metadata is automatically added to indexed chunks:
- `youtube_video_id`  -  the video ID
- `youtube_url`  -  the original video URL
- `youtube_language`  -  transcript language
- `youtube_duration_seconds`  -  total video duration

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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_youtube_v2(
    collection_name="my_collection",
    url="https://www.youtube.com/watch?v=dQw4w9WgXcQ",
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

**collection_name:** `str` — Name of the collection to index into
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
</dd>
</dl>

<dl>
<dd>

**url:** `typing.Optional[str]` — A single YouTube video URL. Supported formats: youtube.com/watch?v=, youtu.be/, youtube.com/shorts/. Provide either 'url' or 'urls', not both.
    
</dd>
</dl>

<dl>
<dd>

**urls:** `typing.Optional[typing.List[str]]` — An array of YouTube video URLs to index (max 20). Provide either 'url' or 'urls', not both.
    
</dd>
</dl>

<dl>
<dd>

**languages:** `typing.Optional[typing.List[str]]` — Preferred transcript languages in priority order (ISO 639-1 codes). Defaults to English. Only specify if you need a non-English transcript (e.g., ['fr', 'de']). Falls back to auto-generated captions if manual transcript unavailable.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_text_v2</a>(...) -> IndexJobResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Index plain text content into a collection.

Accepts raw text content in the request body, saves it as a document, and indexes it for semantic search. No file upload or cloud storage needed.

Text is always processed as basic (no OCR). Ideal for indexing scraped content, notes, articles, or any plain text data.

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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_text_v2(
    collection_name="my_collection",
    content="Machine learning is a subset of artificial intelligence that enables systems to learn and improve from experience...",
    filename="ml_notes.txt",
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

**collection_name:** `str` — Name of the collection to index into
    
</dd>
</dl>

<dl>
<dd>

**content:** `str` — The text content to index.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
</dd>
</dl>

<dl>
<dd>

**filename:** `typing.Optional[str]` — Optional filename for the text document. Defaults to 'snippet-{N}.txt' where N auto-increments.
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">index_file_v2</a>(...) -> IndexJobResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Upload and index files directly into a collection via multipart form-data.

Upload one or more files (max 20) in a single request. Supports PDF, DOCX, XLSX, CSV, TXT, images, and other document types. Files are processed through the same pipeline as cloud storage indexing.

## Supported File Types
PDF, DOCX, DOC, XLSX, XLS, CSV, TSV, TXT, MD, JSON, YAML, YML, PNG, JPG, JPEG, GIF, BMP, TIFF

## Size Limits
- Maximum 100MB per file
- Maximum 20 files per request

## Processing Modes
- **advanced**: AI-enhanced extraction for complex layouts, tables, figures, charts, and documents containing images (2.5 credits/page)
- **basic**: Standard document processing optimized for general indexing (1 credit/page)

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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.index_file_v2(
    collection_name="my_collection",
    files=["example_files"],
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

**collection_name:** `str` — Name of the collection to index into
    
</dd>
</dl>

<dl>
<dd>

**files:** `typing.List[core.File]` — One or more files to upload and index (max 20)
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — UUID for request deduplication
    
</dd>
</dl>

<dl>
<dd>

**processing_type:** `typing.Optional[IndexFileV2RequestProcessingType]` — Document processing type: 'advanced' for AI-enhanced extraction, 'basic' for standard processing
    
</dd>
</dl>

<dl>
<dd>

**custom_metadata:** `typing.Optional[str]` — JSON string of custom metadata to attach to all indexed chunks
    
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

<details><summary><code>client.indexing.<a href="src/runcaptain/indexing/client.py">validate_parsing_script_v2</a>(...) -> ValidateParsingScriptResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Validates a JavaScript parsing script without running it against real data. Upload your .js file as multipart/form-data under the file field. Checks that the script parses cleanly and exports a default function. Use this before uploading a script to catch syntax errors and structural problems. The return-type contract (must return a string) is enforced at indexing time by json_handler against your real JSON.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.indexing.validate_parsing_script_v2(
    file="example_file",
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

**file:** `core.File` — The .js parsing script file to validate. Max 1 MB.
    
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
<details><summary><code>client.jobs.<a href="src/runcaptain/jobs/client.py">get_job_status_v2</a>(...) -> JobStatusResponseV2</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**job_id:** `str` — The job ID returned from an indexing request
    
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

<details><summary><code>client.jobs.<a href="src/runcaptain/jobs/client.py">delete_job_v2</a>(...) -> JobCancelResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel and delete an indexing job.

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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.jobs.delete_job_v2(
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

**job_id:** `str` — The job ID to delete/cancel
    
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

<details><summary><code>client.jobs.<a href="src/runcaptain/jobs/client.py">rollback_job_v2</a>(...) -> JobRollbackResponseV2</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rollback a completed or failed indexing job  -  removes all indexed files and their associated data.

## Behavior
- **Running job**: Returns `409 Conflict`  -  cancel the job first using `DELETE /v2/jobs/{job_id}`
- **Completed/Failed/Cancelled job**: Deletes all files indexed by this job and returns the list of files removed
- **Not found**: Returns `404`

## Use Cases
- Undo a completed indexing job that indexed incorrect data
- Clean up partial data from a failed job
- Remove test data after development/staging indexing runs
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.jobs.rollback_job_v2(
    job_id="abc123xyz-1234567890",
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

**job_id:** `str` — The job ID to rollback
    
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
<details><summary><code>client.datasets.<a href="src/runcaptain/datasets/client.py">search_dataset</a>(...) -> DatasetSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.datasets.search_dataset(
    dataset="nytimes",
    q="latest technology trends",
    limit=10,
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

**q:** `str` — Search query
    
</dd>
</dl>

<dl>
<dd>

**dataset:** `typing.Optional[str]` — The dataset to search. Contact your Account Executive for available datasets.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (default: 10, max: 100)
    
</dd>
</dl>

<dl>
<dd>

**author:** `typing.Optional[str]` — Filter results by author/byline name. Used as an AND condition with `q` â€” returns only articles matching BOTH the query topic AND the specified author. For all articles by an author regardless of topic, use a broad query like `q=*` with `author`.
    
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

<details><summary><code>client.datasets.<a href="src/runcaptain/datasets/client.py">batch_search_datasets</a>(...) -> BatchSearchDatasetsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for articles across multiple news datasets in a single request.

Searches the same query across all specified datasets simultaneously. If no datasets are specified, searches all available datasets.

Contact your Account Executive for available datasets.

## Response
Returns results grouped by dataset source, with title, URL, snippet, author, and date for each article.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.datasets.batch_search_datasets(
    q="artificial intelligence regulation",
    limit=10,
    datasets=[
        "nytimes",
        "washpost",
        "theatlantic"
    ],
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

**q:** `str` — Search query
    
</dd>
</dl>

<dl>
<dd>

**datasets:** `typing.Optional[typing.List[str]]` — List of dataset names to search. Defaults to all datasets if not provided.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (default: 10, max: 100)
    
</dd>
</dl>

<dl>
<dd>

**author:** `typing.Optional[str]` — Filter results by author/byline name. Used as an AND condition with `q`  -  returns only articles matching BOTH the query topic AND the specified author. For all articles by an author regardless of topic, use a broad query like `q=*` with `author`.
    
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

<details><summary><code>client.datasets.<a href="src/runcaptain/datasets/client.py">get_dataset_article</a>(...) -> DatasetArticleResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**url:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**dataset:** `typing.Optional[str]` — The dataset to get articles from. Contact your Account Executive for available datasets.
    
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

<details><summary><code>client.datasets.<a href="src/runcaptain/datasets/client.py">search_medical_papers</a>(...) -> ScientificAskResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search medical and biomedical papers with a natural-language question.
Federates PubMed, PMC full-text, ClinicalTrials.gov, and Semantic Scholar,
then synthesizes a cited answer.

`stream=true` returns text/event-stream with `tool_use`, `tool_result_summary`,
`text_delta`, and `done` event types.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.datasets.search_medical_papers(
    question="What is the evidence that BRCA1-mutated breast cancer patients benefit from PARP inhibitors?",
    max_sources=10,
    include_trials=True,
    recency_years=10,
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

**question:** `str` — Natural-language question.
    
</dd>
</dl>

<dl>
<dd>

**max_sources:** `typing.Optional[int]` — Target number of cited sources in the final answer.
    
</dd>
</dl>

<dl>
<dd>

**include_trials:** `typing.Optional[bool]` — Whether the agent may call ClinicalTrials.gov.
    
</dd>
</dl>

<dl>
<dd>

**recency_years:** `typing.Optional[int]` — Prefer evidence within the last N years where the question allows.
    
</dd>
</dl>

<dl>
<dd>

**stream:** `typing.Optional[bool]` — If true, response is text/event-stream; otherwise JSON.
    
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
<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">search</a>(...) -> GeneralSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cross-entity search across companies and people.

Returns the company match first, then executives (C-suite) at that company, then other employees.

Supports `limit` parameter to control results count (default: 25, max: 100).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.general.search(
    q="AI safety researchers at OpenAI",
    limit=10,
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

**q:** `str` — Search query across all entity types (companies, people, investors)
    
</dd>
</dl>

<dl>
<dd>

**entity_type:** `typing.Optional[GeneralSearchRequestEntityType]` — Filter by entity type
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">search_shared</a>(...) -> GeneralSearchSharedResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Shared/saved search across entities.

Same as cross-entity search with shared filter support. Returns companies and people matching the query.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**q:** `typing.Optional[str]` — Search query (optional)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_people</a>(...) -> GeneralEntityPeopleResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get people associated with an entity (company employees/leadership).

Returns executives first (C-suite, VP, Director), then other employees. Results are deduplicated.

Supports `limit` parameter (default: 25, max: 100).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**entity_id:** `str` — Entity ID (any type)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum results to return (default: 25, max: 100)
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_locations</a>(...) -> GeneralEntityLocationsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**entity_id:** `str` — Entity ID (any type)
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_affiliates</a>(...) -> GeneralEntityAffiliatesResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**entity_id:** `str` — Entity ID (any type)
    
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

<details><summary><code>client.general.<a href="src/runcaptain/general/client.py">entity_news</a>(...) -> GeneralEntityNewsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**entity_id:** `str` — Entity ID (any type)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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
<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">search</a>(...) -> CompaniesSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for companies by name or natural language description.

## Search Modes

- **Direct lookup**: Short queries like `Stripe` or `OpenAI` resolve to a single company match
- **Natural language search**: Longer queries like `AI startups in San Francisco raising Series B` return up to 5 matching companies with surface-level data

The endpoint auto-detects which mode to use based on the query.

## Response Fields

Each result includes: name, website, description, employee_count, industry, location, founded, size, total_funding_raised, latest_funding_stage, tags, and linkedin_url.

Use the entity_id or company identifier from results to call detail endpoints (bio, financing, investors, full).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.companies.search(
    q="OpenAI",
    limit=10,
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

**q:** `str` — Company name, domain, or natural language query (e.g. 'AI startups in San Francisco raising Series B')
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum results (default 5)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">full</a>(...) -> CompaniesFullResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the complete company record with ALL available data fields.

Returns everything: base profile, funding details with amounts and investors, employee analytics and growth rates, executive changes, office locations, job postings, industry classifications, subsidiaries, and more.

Use this after identifying a company via search to get the full picture.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.companies.full(
    company_id="anthropic.com",
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">bio</a>(...) -> CompaniesBioResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">financials</a>(...) -> CompaniesFinancialsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
</dd>
</dl>

<dl>
<dd>

**fiscal_year:** `typing.Optional[int]` — Fiscal year (default: most recent)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">financials_recent</a>(...) -> CompaniesFinancialsRecentResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">financing_recent</a>(...) -> CompaniesFinancingRecentResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">active_investors</a>(...) -> CompaniesActiveInvestorsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">deals</a>(...) -> CompaniesDealsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">service_providers</a>(...) -> CompaniesServiceProvidersResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">service_providers_deal</a>(...) -> CompaniesServiceProvidersDealResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">debt_financing_recent</a>(...) -> CompaniesDebtFinancingRecentResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">similar</a>(...) -> CompaniesSimilarResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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

<details><summary><code>client.companies.<a href="src/runcaptain/companies/client.py">vc_exit_predictions</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get predicted likelihood and timeline for company exit events (IPO or acquisition).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**company_id:** `str` — Company entity ID, website domain, or company name (e.g., 'openai.com', 'OpenAI', or UUID)
    
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
<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">search</a>(...) -> PeopleSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for people by name, company, title, or natural language query. Returns LinkedIn profiles with rich metadata including professional headline, location, bio excerpt, follower count, and school.

Use the returned `entity_id` with `/bio`, `/contact`, or `/education-work` to get full enrichment data.

**Pagination:** Use `offset` and `limit` to page through results. Check `has_more` in the response to determine if more pages are available.

**Large result sets:** Supports up to 500 results per request. For requests exceeding 100 results, the API automatically expands the search with query variations to discover more profiles, then deduplicates by LinkedIn URL.

**Examples:**
- `?q=engineers at Anthropic in San Francisco&limit=20`
- `?q=Sam Altman&limit=1`
- `?q=senior data scientists&company=Stripe&location=New York&limit=50&offset=0`
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.people.search(
    q="engineers at Anthropic in San Francisco",
    limit=5,
    offset=0,
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

**q:** `str` — Person name or search query
    
</dd>
</dl>

<dl>
<dd>

**company:** `typing.Optional[str]` — Filter by current company
    
</dd>
</dl>

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

**limit:** `typing.Optional[int]` — Maximum results per page (1-500). For limits above 100, query expansion is used automatically.
    
</dd>
</dl>

<dl>
<dd>

**offset:** `typing.Optional[int]` — Number of results to skip for pagination. Use with limit to page through results.
    
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

<details><summary><code>client.people.<a href="src/runcaptain/people/client.py">bio</a>(...) -> PeopleBioResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get complete person profile including bio, contact information (emails, phones, social profiles), work history (all positions with companies, titles, dates), and education (schools, degrees, fields of study). One API call returns everything. Use the entity_id from /people/search results.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.people.bio(
    person_id="019d886b-c9e6-745a-b91f-d7ece19a914c",
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

**person_id:** `str` — Person entity ID
    
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
<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">search</a>(...) -> DealsSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**q:** `typing.Optional[str]` — Company name or deal keyword (e.g., 'OpenAI Series B')
    
</dd>
</dl>

<dl>
<dd>

**company:** `typing.Optional[str]` — Filter by company name or domain (e.g., 'OpenAI')
    
</dd>
</dl>

<dl>
<dd>

**deal_type:** `typing.Optional[str]` — Filter by deal type (e.g., 'series_a', 'series_b', 'seed', 'ipo', 'acquisition', 'debt')
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">bio</a>(...) -> DealsBioResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">investors</a>(...) -> DealsInvestorsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">service_providers</a>(...) -> DealsServiceProvidersResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">valuation</a>(...) -> DealsValuationResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">stock_info</a>(...) -> DealsStockInfoResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">cap_table</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get capitalization table showing ownership breakdown after the deal.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">tranche</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get information about deal tranches and payment schedules for structured financing.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">debt_lenders</a>(...) -> DealsDebtLendersResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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

<details><summary><code>client.deals.<a href="src/runcaptain/deals/client.py">multiples</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get valuation multiples for the deal including revenue multiple, EBITDA multiple, and comparable transaction metrics.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Deal entity ID
    
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
<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">search</a>(...) -> InvestorsSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**q:** `typing.Optional[str]` — Investor name or keyword (e.g., 'Sequoia Capital')
    
</dd>
</dl>

<dl>
<dd>

**investor_type:** `typing.Optional[str]` — Filter by investor type
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">bio</a>(...) -> InvestorsBioResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">active_investments</a>(...) -> InvestorsActiveInvestmentsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get current portfolio companies that the investor has active positions in. Returns company names, investment dates, and current status.

Supports pagination via `page` and `page_size` query parameters. Response includes `total_in_database` for the full count across all pages.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number for pagination (default: 1)
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Results per page (default: 50, max: 1000)
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">preferences</a>(...) -> InvestorsPreferencesResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">funds</a>(...) -> InvestorsFundsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">funds_latest</a>(...) -> InvestorsFundsLatestResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">board_seats</a>(...) -> InvestorsBoardSeatsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">service_providers</a>(...) -> InvestorsServiceProvidersResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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

<details><summary><code>client.investors.<a href="src/runcaptain/investors/client.py">service_providers_deal</a>(...) -> InvestorsServiceProvidersDealResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Investor name (e.g., 'Sequoia Capital') or entity ID from /investors/search
    
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
<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">search</a>(...) -> FundsSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.funds.search(
    q="Sequoia Capital Fund",
    limit=10,
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

**q:** `str` — Fund name or keyword (e.g., 'Sequoia Capital Fund XIV')
    
</dd>
</dl>

<dl>
<dd>

**fund_type:** `typing.Optional[str]` — Filter by fund type (e.g., 'venture', 'buyout', 'growth_equity', 'real_estate', 'debt')
    
</dd>
</dl>

<dl>
<dd>

**vintage_year:** `typing.Optional[int]` — Filter by fund vintage year (e.g., 2023)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">bio</a>(...) -> FundsBioResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">performance</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get fund performance metrics including IRR, TVPI, DPI, and RVPI.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">active_investments</a>(...) -> FundsActiveInvestmentsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get current portfolio companies invested by this specific fund. Returns company names, investment amounts, and current status.

Supports pagination via `page` and `page_size` query parameters. Response includes `total_in_database` for the full count across all pages.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number for pagination (default: 1)
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Results per page (default: 50, max: 1000)
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">commitments</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get limited partner commitments to the fund including LP names and commitment amounts. Returns investor base and capital structure.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">cash_flows</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get fund cash flow history including capital calls and distributions.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">benchmark</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get fund performance compared to industry benchmarks and peer funds.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
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

<details><summary><code>client.funds.<a href="src/runcaptain/funds/client.py">preferences</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get investment criteria and preferences for the fund including stage focus, sector preferences, geography, and check size ranges.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**fund_id:** `str` — Fund entity ID
    
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
<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_search</a>(...) -> LpsSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.limited_partners.lps_search(
    q="CalPERS",
    limit=10,
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

**q:** `str` — LP name or keyword (e.g., 'CalPERS')
    
</dd>
</dl>

<dl>
<dd>

**lp_type:** `typing.Optional[str]` — Filter by LP type (e.g., 'pension_fund', 'endowment', 'family_office', 'sovereign_wealth', 'insurance')
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_bio</a>(...) -> LpsBioResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_commitments_detailed</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get detailed fund commitments including specific fund names, commitment amounts, vintage years, and commitment status. Returns complete LP portfolio.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_commitments_aggregates</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get aggregated commitment statistics including total commitments by vintage year, fund type, and geography. Returns high-level allocation summary.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_allocations_target</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get target allocation percentages by asset class, geography, and strategy. Returns investment policy guidelines and target portfolio mix.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_allocations_actual</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get actual current allocation percentages by asset class, geography, and strategy. Returns real portfolio composition and compare to targets.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_commitment_preferences</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get commitment preferences including preferred fund sizes, vintage year focus, and investment stage preferences. Useful for GP fundraising targeting.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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

<details><summary><code>client.limited_partners.<a href="src/runcaptain/limited_partners/client.py">lps_service_providers</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get service providers used by the LP including consultants, custodians, and legal advisors. Returns firm names and service types.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**lp_id:** `str` — LP entity ID
    
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
<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">search</a>(...) -> ServiceProvidersSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.service_providers.search(
    q="Wilson Sonsini",
    limit=10,
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

**q:** `str` — Provider name or keyword (e.g., 'Wilson Sonsini')
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
</dd>
</dl>

<dl>
<dd>

**provider_type:** `typing.Optional[str]` — Filter by provider type (e.g., 'law', 'accounting', 'investment_bank', 'consulting')
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">bio</a>(...) -> ServiceProvidersBioResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**provider_id:** `str` — Service provider entity ID
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">companies</a>(...) -> ServiceProvidersCompaniesResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**provider_id:** `str` — Service provider entity ID
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">deals</a>(...) -> ServiceProvidersDealsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**provider_id:** `str` — Service provider entity ID
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">investors</a>(...) -> ServiceProvidersInvestorsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**provider_id:** `str` — Service provider entity ID
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">funds</a>(...) -> ServiceProvidersFundsResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**provider_id:** `str` — Service provider entity ID
    
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

<details><summary><code>client.service_providers.<a href="src/runcaptain/service_providers/client.py">limited_partners</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Get limited partners that have engaged this service provider. Returns LP clients with service types and relationship details.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**provider_id:** `str` — Service provider entity ID
    
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
<details><summary><code>client.patents.<a href="src/runcaptain/patents/client.py">search</a>(...) -> PatentsSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.patents.search(
    q="machine learning",
    limit=10,
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

**q:** `str` — Patent keyword, assignee, or inventor name
    
</dd>
</dl>

<dl>
<dd>

**assignee:** `typing.Optional[str]` — Filter by assignee (company)
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 10)
    
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

<details><summary><code>client.patents.<a href="src/runcaptain/patents/client.py">get_by_id</a>(...) -> PatentsGetByIdResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get patent details by patent number.

Uses Google Patents search engine to find structured patent data including title, abstract, assignee, inventors, filing date, and publication date.

Returns a direct link to the patent on Google Patents.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**id:** `str` — Patent ID or number
    
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

<details><summary><code>client.patents.<a href="src/runcaptain/patents/client.py">get_file</a>(...) -> PatentsGetFileResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**entity_id:** `str` — Patent entity ID
    
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
<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_search</a>(...) -> CreditAnalysisNewsSearchResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.news_search(
    q="Ares Capital",
    limit=10,
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

**q:** `str` — Search query for credit news (e.g., 'Tesla bond issuance')
    
</dd>
</dl>

<dl>
<dd>

**category:** `typing.Optional[str]` — Filter by news category (e.g., 'bond_issuance', 'rating_change', 'default', 'restructuring')
    
</dd>
</dl>

<dl>
<dd>

**regions:** `typing.Optional[str]` — Filter by region (e.g., 'north_america', 'europe', 'asia')
    
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

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 20)
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_recent</a>(...) -> CreditAnalysisNewsRecentResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**limit:** `typing.Optional[int]` — Maximum number of results to return (1-100, default: 20)
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_detail</a>(...) -> CreditAnalysisNewsDetailResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**news_id:** `str` — News article ID
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_attachment</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

**Coming Soon** - Download attachment files associated with credit news including prospectuses, indentures, and rating reports. Returns document files.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
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

**news_id:** `str` — News article ID
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">news_bulk</a>(...) -> CreditAnalysisNewsBulkResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.news_bulk(
    queries=[
        "Apple credit rating",
        "Tesla debt analysis"
    ],
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

**queries:** `typing.Optional[typing.List[str]]` — List of search queries
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">list_bdcs</a>() -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all tracked Business Development Companies (BDCs). BDCs are publicly traded private credit funds that disclose every loan quarterly in SEC 10-Q/10-K filings.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.list_bdcs()

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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">bdc_search</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search across all indexed BDC portfolios for a borrower, industry, or keyword.

Searches loan-level data from ~50 BDC quarterly filings covering $150B+ in direct loans. Returns matching investments with terms (spread, seniority, maturity, fair value).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.bdc_search(
    q="software",
    seniority="first_lien",
    limit=10,
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

**q:** `str` — Search query  -  borrower name, industry, or keyword
    
</dd>
</dl>

<dl>
<dd>

**seniority:** `typing.Optional[CreditAnalysisBdcSearchRequestSeniority]` — Filter by loan seniority
    
</dd>
</dl>

<dl>
<dd>

**non_accrual_only:** `typing.Optional[bool]` — Only return defaulted (non-accrual) investments
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">bdc_portfolio</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Full Schedule of Investments for a specific BDC, parsed from SEC 10-Q/10-K filings.

Each investment includes: borrower name, industry, investment type, seniority, coupon, spread, reference rate, maturity, principal, fair value, and non-accrual status.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.bdc_portfolio(
    ticker="ARCC",
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

**ticker:** `str` — BDC ticker symbol (e.g., ARCC, BXSL, FSK)
    
</dd>
</dl>

<dl>
<dd>

**quarter:** `typing.Optional[str]` — Quarter like '2025-Q1'  -  defaults to latest filing
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum investments to return
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">bdc_stats</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Aggregate portfolio statistics for a BDC. Returns weighted average spread, non-accrual rate, seniority breakdown, and top industries.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.bdc_stats(
    ticker="ARCC",
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

**ticker:** `str` — BDC ticker symbol
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">borrower_lookup</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cross-BDC borrower lookup  -  find a company across all BDC portfolios.

Returns every BDC that holds this borrower's debt, with position sizes, spreads, and valuations. Reveals syndication patterns and allows cross-lender credit deterioration monitoring.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.borrower_lookup(
    name="Finastra",
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

**name:** `str` — Borrower/company name
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">market_overview</a>() -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Comprehensive private credit market snapshot from free public sources.

Returns:
- **Lending standards** (SLOOS): Net % of banks tightening C&I loan standards
- **Credit spreads**: ICE BofA High Yield, BBB, BB, CCC spreads
- **Bank lending**: Total C&I loans outstanding
- **Interest rates**: 10Y Treasury, SOFR
- **Financial conditions**: St. Louis Financial Stress Index, Chicago NFCI

Data sourced from Federal Reserve (FRED API), updated daily/weekly/quarterly.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.market_overview()

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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">market_spreads</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current and historical credit spread data from ICE BofA indices. Returns High Yield, BBB, BB, and CCC spreads with historical trend.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.market_spreads(
    history=30,
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

**history:** `typing.Optional[int]` — Number of historical data points
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">lending_standards</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Federal Reserve Senior Loan Officer Opinion Survey (SLOOS) data. Shows net % of banks tightening or easing C&I loan standards. Leading indicator for private credit market conditions.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.lending_standards(
    history=20,
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

**history:** `typing.Optional[int]` — Number of quarterly data points
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">funds_search</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search private credit funds via SEC Form D filings. Form D is filed when private funds raise capital under Regulation D. Covers fund formations, managers, and capital raised.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.funds_search(
    q="Ares",
    strategy="direct_lending",
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

**q:** `str` — Fund name, manager name, or keyword
    
</dd>
</dl>

<dl>
<dd>

**strategy:** `typing.Optional[CreditAnalysisFundsSearchRequestStrategy]` — Filter by strategy
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">fund_formations</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Recent private credit fund formations from SEC Form D filings. Shows new funds launching in the private credit space.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.fund_formations(
    days_back=90,
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

**days_back:** `typing.Optional[int]` — Look back period in days
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">list_managers</a>() -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List known private credit fund managers with their strategies and SEC CIK numbers.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.list_managers()

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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">manager_detail</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Detailed information about a private credit fund manager. Combines SEC filing data with known manager intelligence. Returns filing history, fund count, strategy, and recent Form D filings.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.manager_detail(
    name="Ares Management",
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

**name:** `str` — Manager name (e.g., 'Ares Management')
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">sba_search</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search SBA 7(a) loan data. Contains loan-level data with borrower, lender, terms, and performance for 100,000+ loans (FY2020-present).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.sba_search(
    state="CA",
    status="CHGOFF",
    limit=5,
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

**borrower:** `typing.Optional[str]` — Borrower name (partial match)
    
</dd>
</dl>

<dl>
<dd>

**lender:** `typing.Optional[str]` — Bank/lender name (partial match)
    
</dd>
</dl>

<dl>
<dd>

**state:** `typing.Optional[str]` — State code (e.g., CA, NY, TX)
    
</dd>
</dl>

<dl>
<dd>

**naics:** `typing.Optional[str]` — NAICS code prefix (e.g., 5112 for software)
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[CreditAnalysisSbaSearchRequestStatus]` — Loan status: CHGOFF (charged off), PIF (paid in full)
    
</dd>
</dl>

<dl>
<dd>

**min_amount:** `typing.Optional[float]` — Minimum gross approval amount ($)
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">sba_stats</a>() -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Aggregate SBA 7(a) loan statistics. Returns default rates, average loan size, top states, and top industries from 100,000+ indexed loans.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.sba_stats()

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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">agreements_search</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search SEC 8-K filings for credit agreements. When public companies enter material credit facilities, they file the agreement as an exhibit to an 8-K.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.agreements_search(
    borrower="Dell",
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

**borrower:** `typing.Optional[str]` — Borrower/company name
    
</dd>
</dl>

<dl>
<dd>

**lender:** `typing.Optional[str]` — Lender/agent name
    
</dd>
</dl>

<dl>
<dd>

**date_from:** `typing.Optional[str]` — Start date (YYYY-MM-DD)
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">agreement_detail</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the most recent credit agreement filing for a company. Locates the 8-K filing containing the credit agreement.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.agreement_detail(
    company="Alloy",
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

**company:** `str` — Company name
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">nport_funds</a>() -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List tracked private credit interval funds that file N-PORT. These filings contain loan-by-loan holdings.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.nport_funds()

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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">nport_search</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search N-PORT filings for private credit holdings matching a borrower name or keyword.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.nport_search(
    q="Brightstone Capital",
    limit=10,
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

**q:** `str` — Borrower name or keyword
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">nport_fund_filings</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get N-PORT filing list for a specific private credit interval fund.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.nport_fund_filings(
    ticker="CCLFX",
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

**ticker:** `str` — Fund ticker (e.g., CCLFX, AFT)
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">relationships_search</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search lender-borrower relationships across BDC portfolios. Provide either `lender` (to find their borrowers) or `borrower` (to find their lenders).
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.relationships_search(
    lender="Ares Capital",
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

**lender:** `typing.Optional[str]` — Lender name  -  find their borrowers
    
</dd>
</dl>

<dl>
<dd>

**borrower:** `typing.Optional[str]` — Borrower name  -  find their lenders
    
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

<details><summary><code>client.credit_analysis.<a href="src/runcaptain/credit_analysis/client.py">ucc_portals</a>(...) -> typing.Dict[str, typing.Any]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get UCC filing search portal information for free state-level databases. Returns URLs for CA, NY, TX, FL, IL portals and a list of known major private credit lenders.
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.credit_analysis.ucc_portals()

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

**state:** `typing.Optional[str]` — State code (e.g., CA, NY). Omit for all states.
    
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

## SandboxData
<details><summary><code>client.sandbox_data.<a href="src/runcaptain/sandbox_data/client.py">fundamentals_sandbox</a>() -> FundamentalsSandboxResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.sandbox_data.fundamentals_sandbox()

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

<details><summary><code>client.sandbox_data.<a href="src/runcaptain/sandbox_data/client.py">fundamentals_lookup_tables</a>() -> FundamentalsLookupTablesResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.sandbox_data.fundamentals_lookup_tables()

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

<details><summary><code>client.sandbox_data.<a href="src/runcaptain/sandbox_data/client.py">fundamentals_lookup_table_values</a>(...) -> FundamentalsLookupTableValuesResponse</code></summary>
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
from runcaptain.environment import CaptainEnvironment

client = Captain(
    key="<token>",
    organization_id="<X-Organization-ID>",
    environment=CaptainEnvironment.DEFAULT,
)

client.sandbox_data.fundamentals_lookup_table_values(
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

**table_id:** `str` — Lookup table ID
    
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

