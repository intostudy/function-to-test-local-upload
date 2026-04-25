# 🚀 我的 Git & GitHub 极简操作指南

这份文档是我在配置 `某app` 和测试上传时沉淀的经验，防止以后忘记。(ai生成)

---

## 🛡️ 第一部分：安保检查 (非常重要)
在任何推送之前，必须确保隐私文件已被拦截。

### 1. 确认 .gitignore 生效
* **文件名**：必须是 `.gitignore`，不能有 `.txt` 后缀。
* **视觉标志**：在 VS Code 中，被忽略的文件（如 `*.pem`, `*.crt`, `settings.json`）颜色必须是 **灰色**。
* **强制变灰命令**：如果文件已经在 Git 记录中，写了规则也不变灰，运行：
    ```bash
    git rm -r --cached .
    git add .
    ```
    *(这会刷新整个缓存，让所有该变灰的文件瞬间变灰。)*

---

## 🏗️ 第二部分：日常推送三部曲
这是最常用的“无脑”同步流程：

1.  **点名 (Stage)**：把改动加入待发货清单
    ```bash
    git add .
    ```
2.  **打包 (Commit)**：给这次改动贴个标签
    ```bash
    git commit -m "这里写你的更新说明"
    ```
3.  **发射 (Push)**：推送到 GitHub
    ```bash
    git push
    ```

---

## 🛠️ 第三部分：常见报错与急救

### 1. 远程已经存在 (Already exists)
如果报错 `remote origin already exists`，说明地址已经绑过了。想换新地址用：
`git remote set-url origin [新链接]`

### 2. 线上有更新 (Rejected)
如果推送失败，提示 `fetch first`，说明 GitHub 网页端有新东西，先拉再推：
`git pull origin main --rebase`

### 3. 查看当前状态
如果你不确定文件有没有被 Git 盯着，随时输入：
`git status`
* **白色**：提交到暂存。
* **绿色**：新建立的，未打包。
* **灰色**：Git 看不见它（安全）。

---

## 🔗 第四部分：如何提取 Raw 链接给我 (Gemini 调试用)
1.  登录 GitHub 网页，点击目标文件（如 `config.json`）。
2.  点击内容区域右上角的 **[Raw]** 按钮。
3.  复制浏览器地址栏里以 `https://raw.githubusercontent.com/...` 开头的长链接。