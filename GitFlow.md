## Git Flow

`Git`、`Sourcetree`、`constone`、`svn`...

## 名词解释

- **Git**：一个版本控制工具（分布式代码管理系统）
- **Github**：远程仓库的集合体
- **Gitee**：和 `Github` 一样（国内）
- **git 远程仓库**：和本地仓库建立连接
    + 上传、下拉代码
    + 一般在服务器上
- **git 本地仓库**：个人开发者在自己本地创建的仓库
    + 和远程仓库建立连接
- **git 工作区**：开发者写代码的地方
    + 本地仓库的
    + 通过 `add` 指令将修改的代码添加到暂存区
- **git 暂存区**：暂时储存区域
    + 本地仓库的
    + 临时保存修改的位置
    + 通过 `commit` 将修改添加到分支
- **git 分支**：`git` 中最终存储的位置

![Git 版本库的暂存区 stage](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

## 基本指令

- `git init` 初始化本地仓库
- `git clone` 远程拉取代码
- `git status` 查看状态
- `git log` 打印 log 信息
- `git relog` 操作信息
- `git add` 添加到缓存区
- `git diff` 比较工作区与缓存区之间的差异
- `git commit` 提交
- `git branch` 展示分支
- `git checkout` 切换分支
- `git merge` 合并分支
- `git remote` 查看远程信息
- `git push origin dev` 推送分支
- `git reset` 恢复到之前的某一个版本
- `git revert` 创建一个新版本与恢复的版本一致
- `git pull` 拉取最新代码

## 参考资料

[廖雪峰 - 《Git的基本使用》](https://www.liaoxuefeng.com/wiki/896043488029600)

## 本地基本指令

1. **创建本地仓库**

```shell
$ git init
```

2. **将工作区的文件改变提交到缓存区**
    + `.` 提交所有文件
    + `./README.md` 提交某个文件

```shell
$ git add .
```

3. **将缓存区的改变提交到分支**
    + `-m` 注释做了什么事

```shell
$ git commit -m '注释'
```

4. **查看 git 仓库的状态**

```shell
$ git status
```

5. **查看本地分支**
    + `git branch --all` 查看本地所有分支
    + `git branch -a` 查看分支的简写形式

```shell
$ git branch
```

6. **删除分支，不支持自杀式删除**

```shell
$ git branch -d 分支名
```

7. **切换已有分支**

```shell
$ git checkout 分支名
```

8. **创建新的分支并切换**
    + 将当前所在分支做了一份拷贝
    + 形成一个子分支

```shell
$ git checkout -b 分支名
```

9. **在当前分支合并某一分支**（母合并子）
    + 一般都往母体上合并

```shell
$ git merge 分支名
```

10. **查看工作区和暂存区的区别**

```shell
$ git diff
```

11. **打印当前用户操作 git 的信息**
    + `commit` 提交操作

```shell
$ git log
```

12. **打印用户的操作信息**
    + `merge` 合并
    + `checkout` 切换
    + `commit` 提交

```shell
$ git reflog
```

## 远程仓库相关

- `git push origin(仓库名) dev(分支名)`
    + 将本地分支提交到线上
- `git pull origin(仓库名) dev(分支名)`
    + 将线上分支下拉到本地
- `git reset --hard 版本头`
    + 回退到某一版本

#### 1. 远程创建，本地克隆

- `github`、`gitee`、`gitlab`（运维创建）
    + 公司内部搭建的仓库
    + 局域网可以使用
- 通过一个 `README.md` 文件初始化一个仓库
- `git clone 地址`（https）

#### 2. 本地创建，远程连接

- 先通过 `git init` 创建本地仓库
- 创建本地仓库和远程仓库的连接关系
- git remote add origin https://github.com/legion9899/good.git

## 合并分支冲突

- 两个分支相同的部分直接合并
- 不同的部分计算机无法区分选择谁
- 所以将选择权交给开发者
- 这就是冲突

### 解决冲突的方案

- **沟通能不能删**
- 需要的留着
- 不需要的删掉

## .gitignore 忽略文件

- 告诉 `git` 哪些文件需要上传，哪些不需要
- 例如项目中的 `.gitignore` 文件

```shell
.DS_Store
node_modules
/dist

# local env files
.env.local
.env.*.local

# Log files
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Editor directories and files
.idea
.vscode
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?
```

## GitFlow

- 切换分支 / 合并分支
- **`master branch` 主分支**（线上分支）
    + 这里的代码和线上的代码是一样的
- **`Pre-release branch` 预发布分支**
    + 可以和测试分支合成一个
    + 和 `master` 分支保持一致
- **`Test branch` 测试分支**
    + 在上线前进行测试
- **`dev branch` 开发分支**
    + 从 `master` 分支复制
    + 所有开发者在 `dev` 分支进行开发
- **`Personal branch` 个人分支**（功能分支）
    + 从 `dev` 分支复制
    + 做自己的功能开发
- **`bug branch` 漏洞分支**
    + 和线上一致的代码进行复制
- **其他功能分支**

### 具体流程

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