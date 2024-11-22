# Drop Collection​

You can drop a collection if it is no longer needed.​

## Examples​{#examples​}

The following code snippets assume that you have a collection named **customized_setup_2**.​

<Tabs><TabItem value="Python" label="python" default>

```Python
from pymilvus import MilvusClient​
​
client = MilvusClient(​
    uri="http://localhost:19530",​
    token="root:Milvus"​
)​
​
client.drop_collection(​
    collection_name="customized_setup_2"​
)​

```

</TabItem>

<TabItem value="Java" label="java">

```Java
import io.milvus.v2.service.collection.request.DropCollectionReq;​
import io.milvus.v2.client.ConnectConfig;​
import io.milvus.v2.client.MilvusClientV2;​
​
String CLUSTER_ENDPOINT = "http://localhost:19530";​
String TOKEN = "root:Milvus";​
​
// 1. Connect to Milvus server​
ConnectConfig connectConfig = ConnectConfig.builder()​
        .uri(CLUSTER_ENDPOINT)​
        .token(TOKEN)​
        .build();​
​
MilvusClientV2 client = new MilvusClientV2(connectConfig);​
​
DropCollectionReq dropQuickSetupParam = DropCollectionReq.builder()​
        .collectionName("customized_setup_2")​
        .build();​
​
client.dropCollection(dropQuickSetupParam);​

```

</TabItem>

<TabItem value="JavaScript" label="Node.js">

```JavaScript
import { MilvusClient, DataType } from "@zilliz/milvus2-sdk-node";​
​
const address = "http://localhost:19530";​
const token = "root:Milvus";​
const client = new MilvusClient({address, token});​
​
// 10. Drop the collection​
res = await client.dropCollection({​
    collection_name: "customized_setup_2"​
})​
​
console.log(res.error_code)​
​
// Output​
// ​
// Success​
// ​

```

</TabItem>

<TabItem value="Go" label="go">

```Go
import (​
    "context"​
    "fmt"​
    "log"​
​
    "github.com/milvus-io/milvus/client/v2"​
)​
​
ctx, cancel := context.WithCancel(context.Background())​
defer cancel()​
​
milvusAddr := "127.0.0.1:19530"​
token := "root:Milvus"​
​
cli, err := client.New(ctx, &client.ClientConfig{​
    Address: milvusAddr,​
    APIKey:  token,​
})​
if err != nil {​
    log.Fatal("failed to connect to milvus server: ", err.Error())​
}​
​
defer cli.Close(ctx)​
​
err = cli.DropCollection(ctx, client.NewDropCollectionOption("customized_setup_2"))​
if err != nil {​
    // handle error​
}​

```

</TabItem>

<TabItem value="Bash" label="cURL">

```Bash
export CLUSTER_ENDPOINT="http://localhost:19530"​
export TOKEN="root:Milvus"​
​
curl --request POST \​
--url "${CLUSTER_ENDPOINT}/v2/vectordb/collections/drop" \​
--header "Authorization: Bearer ${TOKEN}" \​
--header "Content-Type: application/json" \​
-d '{​
    "collectionName": "customized_setup_2"​
}'​
​
# {​
#     "code": 0,​
#     "data": {}​
# }​

```

</TabItem></Tabs>