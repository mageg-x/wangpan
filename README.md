# 多网盘直链获取工具集合

一个集合多个网盘，获取直链并提供下载接口的Python工具集合。 源码还在整理中, 有需要的话，请提Issue。 

## 功能特性

- 支持多种网盘平台（目前支持TeraBox和Baidu）
- 获取网盘分享链接的直链下载地址
- 提供统一的下载接口
- 支持断点续传下载
- 支持目录上传
- 支持文件分享
- 支持文件转存
- 支持文件列表查看
- 支持文件删除
- 支持文件移动
- 支持目录创建
- 简单易用的API接口

## 支持的网盘

- ✅ TeraBox（原Dubox）
- ✅ Baidu网盘（基础框架已搭建）


## 快速开始

### 1. 配置Cookie

在使用前，您需要获取对应网盘的Cookie信息。

#### TeraBox Cookie获取方法

1. 登录 [TeraBox官网](https://www.terabox.com/)
2. 按F12打开开发者工具
3. 切换到Network标签页
4. 刷新页面
5. 找到一个请求，在Headers标签页中找到Cookie字段
6. 复制完整的Cookie值

#### Baidu网盘 Cookie获取方法

1. 登录 [百度网盘官网](https://pan.baidu.com/)
2. 按F12打开开发者工具
3. 切换到Network标签页
4. 刷新页面
5. 找到一个请求，在Headers标签页中找到Cookie字段
6. 复制完整的Cookie值

### 2. 基本使用

```python
import os
from TeraBox import Terabox

# 配置Cookie
COOKIE = "your_terabox_cookie_here"

# 创建TeraBox实例
tera = Terabox(COOKIE)

# 获取分享链接直链
share_link = "https://1024terabox.com/s/1M6eL1hkvBNxG7bAYjoayeg"
direct_link_info = tera.get_dlink(share_link)
print(f"直链信息: {direct_link_info}")

# 下载文件
download_path = os.getcwd()  # 当前目录
result = tera.download(direct_link_info, download_path)
print(f"下载结果: {result}")
```

## 核心功能接口

**主要方法**
- `get_dlink(link)`: 获取分享链接直链信息
- `download(link_info, save_path)`: 下载文件到指定路径
- `upload_file(local_file, remote_path)`: 上传本地文件到远程路径
- `upload_dir(local_dir, remote_path)`: 上传本地目录到远程路径
- `share_link(path)`: 创建远程文件的分享链接
- `trans_save(link, save_path)`: 将分享文件转存到自己的网盘
- `list_files(path)`: 列出指定路径下的文件列表
- `delete_files(files)`: 删除指定的文件列表
- `move_files(src_paths, dest_paths)`: 移动文件到新路径
- `make_dir(path)`: 创建远程目录

## 项目结构

```
multi-cloud-direct-link/
├── TeraBox/
│   ├── __init__.py    # TeraBox包初始化文件
│   └── terabox.py     # TeraBox核心功能实现
├── Baidu/
│   ├── __init__.py    # Baidu包初始化文件
│   └── baidu.py       # Baidu网盘核心功能实现
├── main.py           # 示例代码和测试文件
└── README.md         # 项目说明文档
```

## 贡献指南

1. Fork 本项目
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 注意事项

1. 本项目仅供学习和研究使用，请遵守各网盘平台的用户协议
2. 不要滥用本工具，以免给网盘平台带来不必要的负担
3. 建议在使用时合理控制请求频率
4. Cookie信息包含您的登录凭证，请妥善保管，不要泄露给他人

## 许可证

MIT License

## 更新日志

### v1.0.0 (2025-12-3)

- 初始版本发布
- 支持TeraBox的完整功能
- 搭建Baidu网盘的基础框架

## 联系方式

如有问题或建议，欢迎提交Issue或Pull Request。
