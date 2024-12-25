# 广东技术师范大学校园网自动登录脚本

这个脚本可以帮助你自动登录广东技术师范大学的校园网。你只需要替换脚本中的 `userId` 和 `password` 为你的学号和密码，然后运行脚本即可。

## 使用方法

1. 安装Python（如果尚未安装）。
2. 安装requests库：`pip install requests`
3. 将以下代码保存为一个Python文件，例如 `auto_login.py`。
4. 运行脚本：`python auto_login.py`

```python
import requests

# 替换为你的学号和密码
user_id = 'your_student_id'
password = 'your_password'

# 登录URL
login_url = 'http://10.0.6.247/eportal/InterFace.do?method=login'

# 查询字符串参数
query_string = (
    'wlanuserip%253D8d7406324f1c4a081bbe1830e7c08ae9'
    '%2526wlanacname%253Da45c52ce92b683ab38b67d6c8965061c'
    '%2526ssid%253D%2526nasip%253Dcf83dc02391d6964087461188367c993'
    '%2526snmpagentip%253D%2526mac%253D8834e90a11332a4d5e5f0df636ef7611'
    '%2526t%253Dwireless-v2%2526url%253D2c0328164651e2b4f13b933ddf36628bea622dedcc302b30'
    '%2526apmac%253D%2526nasid%253Da45c52ce92b683ab38b67d6c8965061c'
    '%2526vid%253D1143f8af8bcfdad6%2526port%253D42d42f607e50cb3d'
    '%2526nasportid%253D5b9da5b08a53a540de3a39287dd9a647149ffd79e11449e6927640363dfdad53a8144d469c3e5115'
)

# 构建登录数据
login_data = {
    'userId': user_id,
    'password': password,
    'service': '',
    'queryString': query_string,
    'operatorPwd': '',
    'operatorUserId': '',
    'validcode': '',
    'passwordEncrypt': 'false'
}

# 发送POST请求进行登录
response = requests.post(login_url, data=login_data)

# 检查响应状态
if response.status_code == 200:
    print('登录成功！')
else:
    print('登录失败，状态码：', response.status_code)
```

## 注意事项

1. 请确保你已经连接到校园网。
2. 每次登录时，请检查网络环境是否与脚本中的查询字符串匹配。
3. 请勿将个人信息暴露在公共平台上，确保脚本中的 `user_id` 和 `password` 仅用于个人使用。

希望这个脚本能帮助你更方便地登录校园网！如果有任何问题或建议，请随时提出。
