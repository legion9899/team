# 组名

Github Team

## 组员

- 单贺喜
- 窦如鑫
- 张博
- 杨泽
- 姜佳欣
- 古吉涛

## 具体流程

1. **主程**
    + 将本地仓库和远程仓库进行关联
    + 从 `master` 分支切分出 `dev` 分支
    + 在 `dev` 分支做项目的架构搭建
    + 将 `dev` 分支上传到远程仓库
2. **路人甲**
    + **接收到第一个任务**
    + 从线上克隆代码
        * `master`
        * `dev`
    + 从 `dev` 分支切分个人分支
    + 在个人分支开发功能
    + **个人分支不做上传，就在自己的电脑上**
    + 切换到 `dev` 合并个人分支
    + **提交之前，优先下拉代码解决冲突**
    + 远程提交 `dev` 分支
    + 删除个人分支
    + **接收到第二个任务**
    + 继续重新执行路人甲流程...
3. **路人乙**
