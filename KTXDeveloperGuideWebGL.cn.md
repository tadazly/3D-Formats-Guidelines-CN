# KTX 2.0 / Basis Universal Textures — WebGL 技巧

为确保从传输纹理格式（即 ETC1S 或 UASTC）到 GPU 压缩格式的转码工作符合预期，开发人员应在各种平台上测试他们的 WebGL 应用程序，因为压缩格式支持方面存在差异。不过，有两种设置提供了极高的兼容性：现代英特尔 GPU（Windows 和 Linux）和苹果 M1 及更新的 SoC（macOS）。

> **警告**：强烈建议使用 Chromium Dev builds 而不是更改 Chrome 或 Edge 的主安装，因为使用非默认 ANGLE 后端可能会降低稳定性或安全性。

## Windows 和 Linux

现代英特尔图形处理器，即英特尔高清显卡 5xx（"Skylake"）或更新版本，在 Windows 和 Linux 上具有最佳的压缩格式覆盖率。要访问 ASTC 和 ETC 格式，需要使用 OpenGL 或 Vulkan。

1. 考虑使用最新的 GPU 驱动程序。在 Windows 上，可以从 [英特尔网站](https://downloadcenter.intel.com/)下载；在 Linux 上，通常由操作系统发行版供应商提供和维护。

2. 安装 [Google Chrome Dev](https://www.google.com/chrome/dev/) 或 [Microsoft Edge Dev](https://www.microsoftedgeinsider.com/en-us/download/).

3.  Windows 上，打开 `about://flags/#use-angle` 页面，选择 OpenGL 作为 ANGLE 图形后端，然后重启浏览器。

4. 在此确认已启用 WebGL 扩展: https://webglreport.com/, the list should include:
   - [`EXT_texture_compression_bptc`](https://www.khronos.org/registry/webgl/extensions/EXT_texture_compression_bptc)
   - [`EXT_texture_compression_rgtc`](https://www.khronos.org/registry/webgl/extensions/EXT_texture_compression_rgtc)
   - [`WEBGL_compressed_texture_astc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_astc)
   - [`WEBGL_compressed_texture_etc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_etc)
   - [`WEBGL_compressed_texture_s3tc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_s3tc)
   - [`WEBGL_compressed_texture_s3tc_srgb`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_s3tc_srgb)

## macOS

Apple M1 和更新的 SoC 支持所有可能的压缩转码目标：BC*、ETC*、ASTC 和 PVRTC1。其中大部分只能通过 Metal API 使用。基于英特尔的 Mac 只支持 BC* 格式。

### 基于 Chromium 的浏览器

1. Install [Google Chrome Dev](https://www.google.com/chrome/dev/) or [Microsoft Edge Dev](https://www.microsoftedgeinsider.com/en-us/download/).

2. Open `about://flags/#use-angle` page, select Metal as ANGLE graphics backend, and restart the browser.

3. 在此确认已启用 WebGL 扩展: https://webglreport.com/, the list should include:
   - [`EXT_texture_compression_bptc`](https://www.khronos.org/registry/webgl/extensions/EXT_texture_compression_bptc)
   - [`EXT_texture_compression_rgtc`](https://www.khronos.org/registry/webgl/extensions/EXT_texture_compression_rgtc)
   - [`WEBGL_compressed_texture_astc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_astc)
   - [`WEBGL_compressed_texture_etc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_etc)
   - [`WEBGL_compressed_texture_pvrtc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_pvrtc)
   - [`WEBGL_compressed_texture_s3tc`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_s3tc)
   - [`WEBGL_compressed_texture_s3tc_srgb`](https://www.khronos.org/registry/webgl/extensions/WEBGL_compressed_texture_s3tc_srgb)

### Safari

1. 确保使用 macOS 12 Monterey 或更新版本。

2. 确保使用 Safari 16 或更新版本。

3. 在此处确认已启用 WebGL 扩展: https://webglreport.com/, 列表应与在 Metal 上运行的基于 Chromium 的浏览器相同。

## Platform Support Table

|                          | AMD                                         | Apple Ax     | Apple M1             | ARM                 | Intel                             | NVIDIA Desktop                           | NVIDIA Tegra | Qualcomm             |
|:------------------------:|---------------------------------------------|--------------|----------------------|---------------------|-----------------------------------|------------------------------------------|--------------|----------------------|
|           ASTC           | ❌                                           | A8 and newer | ✅<sup><b>2</b></sup> | Mali-T620 and newer | Gen9 and newer<sup><b>3</b></sup> | ❌                                        | ✅            | Adreno 3xx and newer |
| BC1<br>BC3<br>BC4<br>BC5 | ✅                                           | ❌            | ✅                    | ❌                   | ✅                                 | ✅                                        | ✅            | ❌                    |
|            BC7           | Radeon HD 5000 and newer<sup><b>1</b></sup> | ❌            | ✅<sup><b>1</b></sup> | ❌                   | Gen7 and newer<sup><b>1</b></sup> | GeForce 400 and newer<sup><b>1</b></sup> | ✅            | ❌                    |
|           ETC1           | ❌                                           | A7 and newer | ✅<sup><b>2</b></sup> | Mali-300 and newer  | Gen8 and newer<sup><b>3</b></sup> | ❌                                        | ✅            | Adreno 2xx and newer |
|        ETC2 / EAC        | ❌                                           | A7 and newer | ✅<sup><b>2</b></sup> | Mali-T6xx and newer | Gen8 and newer<sup><b>3</b></sup> | ❌                                        | ✅            | Adreno 3xx and newer |
|          PVRTC1          | ❌                                           | ✅            | ✅<sup><b>2</b></sup> | ❌                   | ❌                                 | ❌                                        | ❌            | ❌                    |

<p><sup>1</sup> On macOS, only Metal API supports BC7.</p>
<p><sup>2</sup> Use of Metal API is required.</p>
<p><sup>3</sup> Available only on Windows and Linux, requires use of OpenGL or Vulkan.</p>
