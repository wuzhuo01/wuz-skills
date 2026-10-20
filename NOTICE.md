# 第三方工具许可证说明

本仓库只包含 skill 说明文字和脚本（MIT），**不包含、不分发**下列工具的代码或二进制。skill 运行时调用的是使用者本机自行安装的版本。

| 工具 | 用途 | 许可证 |
|---|---|---|
| pngquant / libimagequant | PNG 有损量化 | GPL-3.0（另有商业授权） |
| oxipng | PNG 无损优化 | MIT |
| mozjpeg | JPG 编码 | BSD 类（IJG / 修订版 BSD） |
| dssim | 画质比对 | AGPL-3.0 |

注意：如果将来把这些库**打包进**某个工具一起发布（例如把 libimagequant、dssim 编进 WASM 的单文件网页），那个工具就要按 GPL-3.0 / AGPL-3.0 开源，应放在单独的仓库里，不放进本仓库。

各许可证以工具官方仓库为准。
