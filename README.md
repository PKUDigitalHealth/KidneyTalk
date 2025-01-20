# KidneyTalk 

使用链接：http://kidneytalk.bjmu.edu.cn

[[发布]](https://mp.weixin.qq.com/s/zLhWR9dYOgdF_780vfkACg)
[[功能介绍]](https://mp.weixin.qq.com/s/Hh8sbBbHpdjA3ffCrb7D4A)


## API接口端

兼容OpenAI的API风格，更详细的参数看OpenAI的[官方文档](https://platform.openai.com/docs/api-reference/chat/create)

### 文本模型：`L-72B`
```bash
curl \
    'https://kidneytalk.bjmu.edu.cn/api/v1/chat/completions' \
    -H 'Content-Type: application/json' \
    -d '{
        "model": "L-72B",
        "temperature": 0.5,
        "messages": [
            {
                "role": "user",
                "content": "hello"
            }
        ]
    }'
```


### 视觉模型：`V-72B`
```bash
curl \
    https://kidneytalk.bjmu.edu.cn/api/v1/chat/completions \
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

> 注意：$base64_content必须是图片的base64编码，不接受图片的url形式，因为北大内网机无法联网

### 嵌入模型：`E-72B`
```bash
curl \
	https://kidneytalk.bjmu.edu.cn/api/v1/embeddings \
	-H "Content-Type: application/json" \
	-d '{
		"input": "The food was delicious and the waiter...",
	    	"model": "E-72B",
	    	"encoding_format": "float"
	}'
```
