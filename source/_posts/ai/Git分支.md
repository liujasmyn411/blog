在 Git 中，新建分支、提交文件并合并回主分支是日常开发中最核心的工作流。

以下是标准的操作步骤：

### 1. 创建并切换到新分支
首先，你需要基于当前的 `master` 分支创建一个新分支并切换过去。

```bash
# 确保当前在 master 分支且代码是最新的
git checkout master
git pull origin master

# 创建并切换到新分支 (假设新分支名为 feature-xyz)
git checkout -b feature-xyz
```
*注：`git checkout -b <分支名>` 等同于先执行 `git branch <分支名>` 再执行 `git checkout <分支名>`。*

### 2. 修改文件并提交到新分支
在新分支上进行代码修改，然后将更改提交到**当前分支**（即 `feature-xyz`）。

```bash
# 添加修改过的文件到暂存区
# 添加单个文件：git add 文件名
# 添加所有修改：
git add .

# 提交更改
git commit -m "描述你的修改内容，例如：添加了用户登录功能"
```
此时，提交只存在于本地的 `feature-xyz` 分支上，`master` 分支不受影响。

### 3. 切换回 master 分支
完成新分支的开发和提交后，切换回主分支准备合并。

```bash
git checkout master
```
*建议：在合并前，再次拉取远程最新的代码，避免冲突。*
```bash
git pull origin master
```

### 4. 合并新分支到 master
将刚才开发的分支合并到当前的 `master` 分支。

```bash
git merge feature-xyz
```

**可能出现的情况：**
*   **快进合并 (Fast-forward)**：如果 `master` 在你创建分支后没有新的提交，Git 会直接指针移动，速度很快。
*   **自动合并**：如果两边都有修改但没有冲突，Git 会自动创建一个新的“合并提交”。
*   **合并冲突 (Conflict)**：如果同一文件的同一行被两边修改了，Git 会暂停并提示冲突。你需要手动打开文件解决冲突（保留需要的代码，删除 `<<<<<<<`, `=======`, `>>>>>>>` 标记），然后执行：
    ```bash
    git add <冲突文件>
    git commit -m "解决合并冲突"
    ```

### 5. (可选) 推送到远程仓库
如果你需要将合并后的结果同步到远程服务器，或者之前新建的分支也需要推送到远程：

```bash
# 推送更新后的 master 分支
git push origin master

# 如果是第一次推送新分支 (在步骤2之后，合并之前做也可以)
git push -u origin feature-xyz
```

---

### 现代最佳实践补充：使用 Pull Request (PR) / Merge Request (MR)
在实际的团队开发中（如使用 GitHub, GitLab, Gitee），通常**不直接在本地执行 `git merge`** 然后推送到 `master`，因为这样会绕过代码审查。

**推荐流程：**
1.  本地执行完 **步骤 1** 和 **步骤 2**。
2.  将新分支推送到远程：`git push -u origin feature-xyz`。
3.  去代码托管平台网页端，发起一个 **Pull Request (PR)** 或 **Merge Request (MR)**。
4.  同事在网页上进行代码审查 (Code Review)。
5.  审查通过后，在网页上点击 "Merge" 按钮完成合并。
6.  本地删除旧分支并更新 master：
    ```bash
    git branch -d feature-xyz       # 删除本地分支
    git checkout master
    git pull origin master          # 拉取网页上合并后的最新代码
    ```

### 常用辅助命令
*   查看当前分支状态：`git status`
*   查看分支列表：`git branch` (本地) 或 `git branch -a` (包含远程)
*   查看提交历史图：`git log --oneline --graph --all`