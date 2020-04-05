# Maven

## 读取commons-cli-1.2.jar(或其他jar包)时出错; zip file is empty`

- 原因：jar包有问题，补全或冲突
- 解决：去maven仓库删除对应的jar包后，再重新导入依赖让其自动下载正确的

## build报错：`target\classes: does not exist`

- 原因：target目录被其他程序占用，没被`clean`
- 解决：解放target目录，`clean`后重新build
