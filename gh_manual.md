sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test$ cd theme
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme$ ls
config  dawn-custom  layout  templates  test-kuscs-theme

# プロジェクトディレクトリ作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme$ mkdir gh-cli-test
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme$ ls
config  dawn-custom  gh-cli-test  layout  templates  test-kuscs-theme
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme$ cd gh-cli-test/

# Git初期化
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git init
Initialized empty Git repository in /home/sin3f/sites/kuscs-test/theme/gh-cli-test/.git/
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ ls
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ ls -a
.  ..  .git

# なにかファイルを追加してみる
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ touch README.md

# 隠したいファイルがあれば、.gitignoreを作成し設定する
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ touch .gitignore
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ ll
total 16
drwxr-xr-x 3 sin3f sin3f 4096 Oct 22 21:28 ./
drwxr-xr-x 8 sin3f sin3f 4096 Oct 22 21:24 ../
drwxr-xr-x 7 sin3f sin3f 4096 Oct 22 21:26 .git/
-rw-r--r-- 1 sin3f sin3f    0 Oct 22 21:28 .gitignore
-rw-r--r-- 1 sin3f sin3f   17 Oct 22 21:28 README.md

# 作ったファイルをステージに追加
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git add .

# ローカルのリポジトリの状態をチェック
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   .gitignore
        new file:   README.md

# GITコミット
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git commit -m "First Commit"
[master (root-commit) dabaa4c] First Commit
 2 files changed, 1 insertion(+)
 create mode 100644 .gitignore
 create mode 100644 README.md

 # リポジトリ作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh repo create
? Repository name gh-cli-test
? Repository description GitHub CLI Test Repo.
? Visibility Public
? This will add an "origin" git remote to your local repository. Continue? Yes
✓ Created repository kuscs-shin/gh-cli-test on GitHub
✓ Added remote https://github.com/kuscs-shin/gh-cli-test.git

# リモートリポジトリができたか確認
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git remote -v
origin  https://github.com/kuscs-shin/gh-cli-test.git (fetch)
origin  https://github.com/kuscs-shin/gh-cli-test.git (push)

# ローカルリポジトリに、developという名前の新しいブランチをチェックアウト
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git checkout -b develop
Switched to a new branch 'develop'

# ローカルで作成したブランチをリモートのdevelopブランチにpush
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git push -u origin develop
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 272 bytes | 272.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To https://github.com/kuscs-shin/gh-cli-test.git
 * [new branch]      develop -> develop
Branch 'develop' set up to track remote branch 'develop' from 'origin'.

# リモートブランチができたかブラウザで確認
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh repo view --web
Opening github.com/kuscs-shin/gh-cli-test in your browser.

# issue作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh issue create

Creating issue in kuscs-shin/gh-cli-test

? Title To fix README.md
? Body <Received>
? What's next? Submit
https://github.com/kuscs-shin/gh-cli-test/issues/1

# issueの確認
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh issue list

Showing 1 of 1 open issue in kuscs-shin/gh-cli-test

#1  To fix README.md    less than a minute ago

# CLIでissue作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh issue create --title "Issue created from CLI" --body "TEST CREATE issue 2" 
Creating issue in kuscs-shin/gh-cli-test

https://github.com/kuscs-shin/gh-cli-test/issues/2

# issueの確認
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh issue list
Showing 2 of 2 open issues in kuscs-shin/gh-cli-test

#2  Issue created from CLI    less than a minute ago
#1  To fix README.md          about 4 minutes ago

# PullRequest用のブランチを新規作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git checkout -b 'try-pr1-create'
Switched to a new branch 'try-pr1-create'

# PullRequestファイルを作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ touch pr1.md
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git add pr1.md

# PullRequestファイルをステージに追加
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ commit -m "Add Pr1.md"
commit: command not found

# PullRequestファイルをステージに追加
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git commit -m "Add Pr1.md"
[try-pr1-create a84fb8c] Add Pr1.md
 1 file changed, 1 insertion(+)
 create mode 100644 pr1.md

# GitHubにPullRequestを作成
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh pr create
Warning: 1 uncommitted change
? Where should we push the 'try-pr1-create' branch? kuscs-shin/gh-cli-test

Creating pull request for try-pr1-create into develop in kuscs-shin/gh-cli-test

? Title Add Pr1.md
? Body <Received>
? What's next? Submit
remote: 
remote: 
To https://github.com/kuscs-shin/gh-cli-test.git
 * [new branch]      HEAD -> try-pr1-create
Branch 'try-pr1-create' set up to track remote branch 'try-pr1-create' from 'origin'.
https://github.com/kuscs-shin/gh-cli-test/pull/3

# GitHubのPullRequestを確認
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh pr list

Showing 1 of 1 open pull request in kuscs-shin/gh-cli-test

#3  Add Pr1.md  try-pr1-create

# PullリクエストのDiff
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh pr diff 3
diff --git a/pr1.md b/pr1.md
new file mode 100644
index 0000000..c47eef5
--- /dev/null
+++ b/pr1.md
@@ -0,0 +1 @@
+# Pull Request Create Test


sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git chekuout 'develop'
git: 'chekuout' is not a git command. See 'git --help'.

The most similar command is
        checkout
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git checkuout 'develop'
git: 'checkuout' is not a git command. See 'git --help'.

The most similar command is
        checkout
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ git checkout 'develop'
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh pr diff 3
diff --git a/pr1.md b/pr1.md
new file mode 100644
index 0000000..c47eef5
--- /dev/null
+++ b/pr1.md
@@ -0,0 +1 @@
+# Pull Request Create Test
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh co 3
Switched to branch 'try-pr1-create'
Your branch is up to date with 'origin/try-pr1-create'.
Already up to date.
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ gh co 2
GraphQL error: Could not resolve to a PullRequest with the number of 2.
sin3f@DESKTOP-C17T6NV:~/sites/kuscs-test/theme/gh-cli-test$ 