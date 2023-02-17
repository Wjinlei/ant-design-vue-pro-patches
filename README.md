### 补丁介绍
该补丁用于修改 `ant-design-vue-pro` 项目成`我想要的结构`。  
它将把项目对于 `src/api`、`src/mock/services`、`src/views` 的引用修改到 `example`目录中。  

### 自动处理
1、先应用`补丁0001`，它将把项目对于 `src/api`、`src/mock/services`、`src/views` 的引用修改到 `example`目录中。
2、再应用`补丁0002` 或者 手动处理目录结构，它将实际移动上面的目录到对应的`example`目录中。

### 手动处理目录结构
1. 将 `src/api` 目录中的文件移动到 `src/api/example` 目录中
2. 将 `src/mock/services` 目录中的文件移动到 `src/mock/services/example` 目录中
3. 将 `src/views` 目录中的文件移动到 `src/views/example` 目录中，并保留 `src/views/exception` 、`src/views/user` 目录

`views`目录最终结构

	- `src/views/example`
	- `src/views/exception`
	- `src/views/user`
	- `src/views/Dashboard.vue`

### 注意事项：
- 如果应用了`补丁0002`，就不用手动处理目录结构了，如果不应用`补丁0002`就需要手动处理目录结构

- 由于`补丁0002`包含了复制`example`目录的`exception`目录和`user`目录的内容到上级的操作，  
这在`Git`中属于添加内容的行为，添加的代码是固定的。  
而未来`antd`代码可能发生变更（`exception`目录和`user`目录代码可能发生变更），  
因此不能保证`100%`随着项目的更新代码是最新的。所以，我建议手动处理目录结构。

- `src/util/request.js` 添加了一个`messageHandler` 如果不需要可自行修改或删除。