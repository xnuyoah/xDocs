## python使用requests库提交multipart/form-data请求

[python使用requests库提交multipart/form-data请求](https://blog.csdn.net/qq_44159028/article/details/119890079)

```python
import requests


headers = {
    "Accept": "*/*",
    "Accept-Language": "zh-CN,zh;q=0.9",
    "^Authorization": "^%^7B^%^22real_ipd^%^22^%^3A^%^22124.77.254.34^%^22^%^2C^%^22ECS_ID^%^22^%^3A^%^22fcb619ee9a430d20c56d6cc5a89d18349bb103bb^%^22^%^2C^%^22ECS^%^22^%^3A^%^5B^%^5D^%^7D^",
    "Cache-Control": "no-cache",
    "Connection": "keep-alive",
    # "Content-Type": "multipart/form-data; boundary=----WebKitFormBoundaryuKeOH6INqtHZb5fd",
    "Origin": "https://www.solarbio.com",
    "Pragma": "no-cache",
    "Referer": "https://www.solarbio.com/categoryList?id=102",
    "Sec-Fetch-Dest": "empty",
    "Sec-Fetch-Mode": "cors",
    "Sec-Fetch-Site": "same-origin",
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36",
    "^sec-ch-ua": "^\\^Google",
    "sec-ch-ua-mobile": "?0",
    "^sec-ch-ua-platform": "^\\^Windows^^^"
}
cookies = {
    "Hm_lvt_de7d9a5bd7d887244ee0370b4975008c": "1711607910",
    "__root_domain_v": ".solarbio.com",
    "_qddaz": "QD.622211607909843",
    "_qdda": "3-1.1",
    "_qddab": "3-6313qc.luaxypy7",
    "Hm_lpvt_de7d9a5bd7d887244ee0370b4975008c": "1711613117"
}
url = "https://www.solarbio.com/web/lists/category/goods"
data = {
    "id": (None, 102),
    "page": (None, 1),
    "size": (None, 10)
}
response = requests.post(url, headers=headers, cookies=cookies, files=data, verify=False)

print(response.text)
print(response)
```

