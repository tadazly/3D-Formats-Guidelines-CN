# KTX 2.0 工具

[KTX-Software](https://github.com/KhronosGroup/KTX-Software/) 提供用于读取、写入和转码 KTX 文件的官方 C/C++/WASM 库，包括 [可下载的二进制包](https://github.com/KhronosGroup/KTX-Software/releases) 和在线 [文档]](https://github.khronos.org/KTX-Software/).

*有关用于 KTX 2.0 相关特定任务的其他项目，请参阅下面的功能部分。*

## 读/写 KTX 纹理

- [Binomial Encoder](https://github.com/BinomialLLC/basis_universal): 二项式 C/C++、WASM 和 CLI 编码器，用于 Basis UASTC 和 ETC1S 纹理模式。
- [KTX-Parse](https://github.com/donmccurdy/KTX-Parse): 用于读写 KTX 文件的轻量级 JavaScript/TypeScript/Node.js 库。转码为 GPU 压缩格式必须单独处理。
- [Kram](https://github.com/alecazam/kram) 可用于将 BC/ETC2/ASTC 文件编码和捆绑为 KTX/KTX2。使用 libktx 工具为 KTX2 和 Basis 文件提供脚本支持。Windows/macOS 二进制版本。

## 将 KTX 转码为 GPU 格式

- [Binomial Transcoder](https://github.com/BinomialLLC/basis_universal): 用于 Basis UASTC 和 ETC1S 纹理模式的二项式 C/C++ 和 WASM 转码器。
- [Khronos Transcoders](https://github.com/KhronosGroup/Basis-Universal-Transcoders): 轻量级 WASM 转码器，用于 Basis UASTC 纹理模式。

## 查看 KTX 纹理

- [BabylonJS Sandbox](https://sandbox.babylonjs.com/): 允许用户查看独立的 KTX 纹理，或使用嵌入式 KTX 纹理的 glTF 模型。
- [Gestaltor Editor](https://gestaltor.io/): 支持 KTX 读/写的可视化 glTF 编辑器。
- [Image Viewer and Tonemapper](https://github.com/kopaka1822/ImageViewer): 可用于查看、图像比较和统计、色调映射和 mipmap 生成。该程序具有试验性的 KTX 2 支持。仅限 Windows。

## 在 glTF 3D 模型中使用 KTX 纹理

- [Gestaltor Editor](https://gestaltor.io/): 支持 KTX 读/写的可视化 glTF 编辑器。
- [gltf-transform](https://gltf-transform.donmccurdy.com/cli.html): CLI 工具，可将 glTF 模型的纹理转换为 KTX。
- [gltfpack](https://github.com/zeux/meshoptimizer/tree/master/gltf): CLI 工具，可将 glTF 模型的纹理转换为 KTX。
- [glTF-Compressor](https://github.khronos.org/glTF-Compressor-Release/): 支持 KTX 读/写的可视化 glTF 编辑器。
- [RapidCompact](https://rapidcompact.com/): 优化 3D 数据的在线平台。
