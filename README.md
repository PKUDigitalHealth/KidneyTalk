# KidneyTalk 

http://202.112.180.149/#/chat

仅北医内网可以调用。兼容OpenAI的API风格，更详细的参数看OpenAI的[官方文档](https://platform.openai.com/docs/api-reference/chat/create)

### 文本模型：`L-72B`
```bash
curl \ 
	http://202.112.180.149/api/v1/chat/completions \
    -H "Content-Type: application/json" \
    -d '{
	        "model": "L-72B",
	        "messages": [
	            {"role": "user", "content": "什么是CDK"}
	        ]
    }'
```


### 视觉模型：`V-72B`
```bash
curl \
    http://202.112.180.149/api/v1/chat/completions \
    -H "Content-Type: application/json" \
    -d '{
        "model": "VL-72B", 
        "messages": 
            [
                {
                    "role": "system", 
                    "content": "你是一名化验单解读专家"
                },
                {
                    "role": "user", 
                    "content": [
                        {
                            "type": "image_url", 
                            "image_url": {"url": "$base64_content"}
                        },
                        {
                            "type": "text", 
                            "text": "化验单中存在异常值吗？"
                        }
                    ]
                }
            ]
    }'
```

### 嵌入模型：`E-72B`
```bash
curl \
	http://202.112.180.149/api/v1/embeddings \
	-H "Content-Type: application/json" \
	-d '{
		"input": "The food was delicious and the waiter...",
	    "model": "E-72B",
	    "encoding_format": "float"
	}'
```
