# zlib 示例程序与文档说明

本目录包含 zlib 库的使用示例、相关程序及文档。

*   **enough.c**
    *   **功能：** 计算并验证 `inftrees.h` 头文件中 `ENOUGH` 参数的值。
    *   **说明：** 计算在构建解压缩树（inflate tree）过程中，针对所有可能的霍夫曼编码（Huffman codes），所需的最大表空间。

*   **fitblk.c**
    *   **功能：** 仅压缩足够多的输入数据，使其压缩后的输出大小尽可能接近指定的目标大小。
    *   **说明：** zlib 本身并非为此类需求设计，但此示例展示了如何实现。

*   **gun.c**
    *   **功能：** 解压缩 gzip 文件。
    *   **说明：**
        *   演示如何利用回调函数（call-back functions）调用 `inflateBack()` 实现高速的文件到文件解压。
        *   解压速度约为 `gzip -d` 的两倍。
        *   同时提供 Unix `uncompress` 功能，速度同样快一倍。

*   **gzappend.c**
    *   **功能：** 向现有 gzip 文件追加数据。
    *   **说明：**
        *   演示 `inflate()` 函数中 `Z_BLOCK` 刷新参数的使用。
        *   演示 `deflatePrime()` 函数如何从任意比特位开始压缩。

*   **gzjoin.c**
    *   **功能：** 合并多个 gzip 文件，无需重新计算 CRC 校验值或重新压缩数据。
    *   **说明：**
        *   演示 `inflate()` 函数中 `Z_BLOCK` 刷新参数的使用。
        *   演示 `crc32_combine()` 函数的使用。

*   **gzlog.c / gzlog.h**
    *   **功能：** 高效且健壮地维护 gzip 格式的日志文件。
    *   **说明：**
        *   演示原始 deflate 格式（raw deflate）、`Z_PARTIAL_FLUSH`、`deflatePrime()` 和 `deflateSetDictionary()` 的使用。
        *   演示 gzip 头文件中额外字段（extra field）的使用。

*   **gznorm.c**
    *   **功能：** 通过将多个成员合并为单一成员来规范化 gzip 文件。
    *   **说明：** 演示如何利用 `Z_BLOCK` 参数连接多个 deflate 数据流。

*   **zlib_how.html**
    *   **功能：** 对 `zpipe.c` (见下文) 极其详尽的说明文档。
    *   **说明：** 深入细致地描述了 `deflate()` 和 `inflate()` 函数的使用方法。

*   **zpipe.c**
    *   **功能：** 从标准输入读取数据并压缩/解压缩，将结果写入标准输出。
    *   **说明：**
        *   演示 `deflate()` 和 `inflate()` 函数的正确用法。
        *   其详细注释请参见 `zlib_how.html` (见上文)。

*   **zran.c / zran.h**
    *   **功能：** 为 zlib 或 gzip 数据流创建索引并支持随机访问。
    *   **说明：** 演示如何结合使用 `Z_BLOCK`、`inflatePrime()` 和 `inflateSetDictionary()` 来实现随机访问功能。