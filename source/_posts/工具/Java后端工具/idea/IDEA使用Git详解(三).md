---
title: IDEA 使用 Git 详解(三)
tags:
  - IDEA
categories:
  - 工具
description: IDEA 使用 Git 详解(三)
top_img: >-
  https://boosterminiclass.com/wp-content/uploads/2023/07/intellij_idea_git_2.png
cover: >-
  https://boosterminiclass.com/wp-content/uploads/2023/07/intellij_idea_git_2.png
date: '2024-09-25 14:45:04' 
abbrlink: d06fc5d7
---

![ https://n.sinaimg.cn/sinakd10116/612/w2000h1012/20200629/34e0-ivrxcex3246619.jpg](https://n.sinaimg.cn/sinakd10116/612/w2000h1012/20200629/34e0-ivrxcex3246619.jpg)

## 管理 Git 分支

在 Git 中，分支是一种强大的机制，它允许您偏离主开发线，例如，当您需要处理[某个功能](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#feature-branches)，或者冻结代码库的某个状态以进行发布等时。

在 IntelliJ IDEA 中，所有分支操作都在Git Branches弹出窗口中执行。要调用它，请在主窗口标题中单击包含当前签出的分支名称的 Git 小部件：

![Git 小部件](https://intellijidea.com.cn/help/img/idea/2023.2/git_widget.png)

您还可以在Git工具窗口的[“分支”窗格](https://intellijidea.com.cn/help/idea/log-tab.html#BranchesPane)中管理分支并对多个分支执行批量操作。

![分支窗格](https://intellijidea.com.cn/help/img/idea/2023.2/branches_pane.png)



**1、创建新分支**﻿

> **从当前分支创建一个新分支**﻿
>
> 1. 在“分支”弹出窗口中，选择“新建分支”或右键单击 Git工具窗口的“分支”窗格中的当前分支，然后从“分支名称”中选择“新建分支” 。
>
> 2. 在打开的对话框中，指定分支名称，如果要切换到该分支，请确保选择“签出分支”选项。
     >
     >    一旦您开始为新分支输入名称，IntelliJ IDEA 将根据现有本地分支的名称建议相关前缀。
     >
     >    新分支将从当前分支 HEAD 开始。

> **从选定的分支创建新分支**﻿
>
> 1. 在“分支”弹出窗口或 Git工具窗口的“分支”窗格中，选择要从中启动新分支的本地或远程分支，然后从“选定的”中选择“新建分支”。
> 2. 在打开的对话框中，指定分支名称，如果要切换到该分支，请确保选择“签出分支”选项。

> **从选定的提交创建新分支**﻿
>
> 1. 在[“日志”视图](https://intellijidea.com.cn/help/idea/log-tab.html)中，选择要充当新分支起点的提交，然后从上下文菜单中选择“新建分支” 。
> 2. 在打开的对话框中，指定分支名称，如果要切换到该分支，请确保选择“签出分支”选项。



**2、重命名分支**﻿

> 1. 在“分支”弹出窗口或 Git工具窗口的“分支”窗格中，选择要重命名的分支，然后选择“重命名”。
> 2. 在打开的对话框中，将分支名称更改为您需要的名称。
>
> 要复制分支的名称，请将鼠标悬停在该分支上并按。`Ctrl` `C`



**3、将分支标记为收藏夹**﻿

> 如果您有很多分支，您可能只想查看您最喜欢的分支。默认情况下，主分支被标记为收藏夹。最喜欢的分支始终显示在“分支”弹出窗口的顶部以及 Git工具窗口的“分支”窗格中。
>
> - 要将分支标记为收藏夹，请在“分支”弹出窗口中，将鼠标悬停在分支名称上，然后单击左侧显示的星形轮廓：
    >
    >   ![最喜欢的分支](https://intellijidea.com.cn/help/img/idea/2023.2/GitFavoriteBranch.png)
    >
    >   或者，选择您想要标记为收藏的分支，然后按Space。
    >
    >   您还可以在Git工具窗口的“分支”窗格中选择一个分支 ，然后单击工具栏上的 。![星形图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.nodes.favorite.svg)
>
> > 在搜索特定分支并导航分支列表时，按将焦点移回搜索字段。`Ctrl` `F`



**4、集团分支机构**﻿

在“分支”弹出窗口中，IntelliJ IDEA 将分支保留在三个节点中：



- 最近的分支节点最多显示五个最近签出的分支。
- 本地分支节点列出了所有本地分支。
- 远程分支节点显示最新[fetch](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)之后可用的所有远程分支。



此外，IntelliJ IDEA 自动按前缀对分支进行分组并将它们存储在可扩展列表中。

![在“分支”弹出窗口中按前缀分组的分支](https://intellijidea.com.cn/help/img/idea/2023.2/branches_grouped_by_prefix.png)

为了对分支进行分组，分支名称中的前缀应使用正斜杠分隔/。例如，`jd/2023.1`。

如果您不希望按前缀对分支进行分组，请单击“分支”![齿轮图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.settings.svg)弹出窗口右上角的，然后取消选择“按前缀分组”选项以将其禁用。

![“分支”弹出窗口中的“按前缀分组”选项](https://intellijidea.com.cn/help/img/idea/2023.2/group_by_prefix_option.png)



**5、检查分支（git-checkout）**﻿

如果您想处理其他人创建的分支，则需要将其签出以创建该分支的本地副本。

要确保您拥有远程分支的完整列表，请单击“分支”![获取图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.expui.vcs.fetch.svg)弹出窗口：

![获取图标](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_fetch_from_branches_popup.png)

> **将分支检出为新的本地分支**﻿
>
> 1. 在“分支”弹出窗口或 Git工具窗口的“分支”窗格中，选择要从“远程分支”或“公共远程分支”（如果您的项目有多个根并且启用了[同步分支控制）在本地检出的分支，或者从](https://intellijidea.com.cn/help/idea/manage-branches.html#synchronous_branch_control)“存储库”| 远程分支（如果已禁用）。
> 2. 从操作列表中选择结帐。
>
> 将创建、检出并设置新的本地分支以跟踪原始远程分支。
>
> 您可能已经有一个与您要签出的远程分支同名的本地分支。根据具体情况，您可以通过以下方式完成结账流程：
>
>
>
> - 如果没有提交丢失，并且本地分支已经跟踪远程分支，IntelliJ IDEA 会自动将本地分支重置为远程分支，然后将其签出。
> - 如果本地分支包含可能因重置而丢失的提交，IntelliJ IDEA 将为您提供：
    >   - 删除本地提交：IntelliJ IDEA 将删除您的本地提交、重置本地分支并更改跟踪。
>   - 变基到远程：IntelliJ IDEA 会将您的本地分支变基到远程分支，保留本地提交，重置本地分支并更改跟踪。

> **分支间切换**﻿
>
> 当[进行多任务处理](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html)时，您经常需要在分支之间跳转以提交不相关的更改。
>
> 1. 在“分支”弹出窗口或 Git工具窗口的“分支”窗格中，在“本地分支”下选择要切换到的分支，然后从可用操作列表中选择“签出” 。
     >
     >    对于多存储库项目，分支会按存储库自动分组。要检查必要的分支，请在“分支”弹出窗口中，首先选择存储库。
>
> 2. 接下来会发生什么取决于您尚未提交的本地更改与您要签出的分支之间是否存在冲突：
     >
     >    - 如果你的工作树是干净的（这意味着你没有未提交的更改），或者你的本地更改与指定分支不冲突，则该分支将被签出（IntelliJ IDEA 右下角会弹出通知）窗户）。
>
>    - 如果您的本地更改将被签出覆盖，IntelliJ IDEA 会显示阻止您签出所选分支的文件列表，并建议在Force Checkout和Smart Checkout之间进行选择。
       >
       >      > 如果您单击“强制签出”，您本地未提交的更改将被覆盖，并且您将丢失它们。
       >      >
       >      > 如果您单击Smart Checkout，IntelliJ IDEA 将[搁置](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#shelve)未提交的更改，检出所选分支，然后取消搁置更改。如果取消搁置操作期间发生冲突，系统将提示您合并更改。有关详细信息，请参阅[解决冲突](https://intellijidea.com.cn/help/idea/resolve-conflicts.html)。
       >      >
       >      >     > 如果您想使用[存储](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#stash)而不是搁置来清理工作副本，请转到版本控制| IDE 设置的 Git页面，然后在“清理工作树使用”设置下选择“搁置”。`Ctrl` `Alt` `S`
>
> > IntelliJ IDEA 会保存您的[上下文](https://intellijidea.com.cn/help/idea/managing-tasks-and-context.html#work-with-context)（一组打开的文件、当前运行配置和[断点](https://intellijidea.com.cn/help/idea/using-breakpoints.html)），前提是在“版本控制”| “设置”对话框中启用了“分支切换时恢复工作区”选项。确认。当您切换到分支时，IntelliJ IDEA 会自动恢复与该分支关联的上下文。`Ctrl` `Alt` `S`



**6、比较分支机构**﻿

> **将分支与当前分支进行比较**﻿
>
> 如果你想检查一个分支与当前分支的分歧程度，你可以比较它们。
>
> 1. 从“分支”弹出窗口或 Git工具窗口的“分支”窗格中，选择要与当前分支进行比较的分支，然后选择“与当前比较”。
     >
     >    Git工具窗口中将添加一个新选项卡，列出所选分支中存在且当前分支中不存在的所有提交。
     >
     >    您可以单击“交换分支”链接来更改将哪个分支视为与其他分支进行比较的基础。
>
> 2. 要查看两个分支中不同的所有文件的列表，请单击：[“更改的文件”窗格](https://intellijidea.com.cn/help/idea/log-tab.html#changedFiles)将列出包含差异的所有文件。`Ctrl` `A`

> **将分支与工作树进行比较**﻿
>
> 除了将分支与当前分支进行比较之外，您还可以将其与当前分支的本地状态进行比较。如果您有本地未提交的更改，这非常有用。
>
> - 从“分支”弹出窗口或 Git工具窗口的“分支”窗格中，选择要与本地工作树进行比较的分支，然后选择“显示与工作树的差异”。
    >
    >   打开的“更改”工具窗口显示所选分支中与当前签出的分支相比不同的所有文件的列表：
    >
    >   ![显示所选分支和当前工作树之间的差异](https://intellijidea.com.cn/help/img/idea/2023.2/ij_git_branches_diff.png)
    >
    >   - 所选分支中存在且当前分支中缺失的文件标记为灰色。
>   - 当前分支中存在但所选分支中缺失的文件标记为绿色。
>   - 包含所选分支和当前分支之间差异的文件用蓝色标记。
    >
    >   您可以单击“交换分支”链接来更改将哪个分支视为与其他分支进行比较的基础。
    >
    >   - 要查看特定文件中的差异，请选择该文件并单击![差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)工具栏上的 ，或按。`Ctrl` `D`
>   - 要将整个文件内容应用到当前分支，请单击![从分支获取图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.download.svg)。有关详细信息，请参阅[应用单独的文件](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#copy-files-to-branch)。

**7、删除分支**﻿

> 将功能分支的[更改集成](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html)到开发主线后，您可以删除不再需要的分支。
>
> 1. 检查您将用于进一步工作的分支。
> 2. 在“分支”弹出窗口中或从 Git工具窗口的“分支”窗格中，右键单击要删除的分支，然后选择“删除”。
>
> 删除分支后，右下角会显示一条通知，您可以从中恢复已删除的分支：
>
> ![删除分支通知](https://intellijidea.com.cn/help/img/idea/2023.2/deleted_branch_notification.png)
>
> 如果分支包含尚未合并到其上游分支或当前分支的提交，它仍然会立即删除（相当于 or 命令`git branch --D`）`git branch --delete --force`，但通知还将包含一个链接，允许您查看未合并的提交。
>
> 如果删除的分支正在跟踪远程分支，则此通知中还会有一个用于删除远程分支的链接。
>
> > [如果您已关闭通知并稍后决定恢复已删除的分支，则该链接将在“通知”工具窗口](https://intellijidea.com.cn/help/idea/notifications.html)中可用，直到您重新启动 IntelliJ IDEA。



**8、配置同步分支控制**﻿

> 如果您有一个多根存储库，您可以将 IntelliJ IDEA 配置为在所有根上同时执行所有分支操作（例如签出、合并、删除等），就像它是单个存储库一样。
>
> 1. 按打开 IDE 设置，然后选择版本控制 | 吉特.`Ctrl` `Alt` `S`
> 2. 选择“在所有根上执行分支操作”选项（请注意，此选项仅在您的项目有多个根时才可用）。
>
> 如果某个操作至少在其中一个存储库中失败，IntelliJ IDEA 会建议您在成功的存储库中回滚此操作，从而防止分支出现分歧。
>
> > 如果您仅在其中一个根上检查分支，IntelliJ IDEA 将在“分支”弹出窗口中显示“分支已发散”警告。这意味着根项目位于不同的分支上。
> >
> > 如果您想继续，请忽略此警告或禁用“在所有根上执行分支操作”选项。如果您仍想同时对所有根执行分支操作，请手动检查其余存储库中的同名分支。



## 将更改从一个 Git 分支应用到另一分支

在 Git 中，有多种方法可以将一个分支的更改集成到另一个分支：

- [合并分支](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)
- [变基分支](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)
- [挑选单独的提交](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#cherry-pick)
- [应用提交中的单独更改](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#apply-separate-changes)
- [将特定文件应用到分支](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#copy-files-to-branch)



**1、合并分支**﻿

假设您创建了一个[功能分支](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#feature-branches)来处理特定任务，并希望在完成并测试功能后将工作结果集成到主代码库中：

![特征分支图](https://intellijidea.com.cn/help/img/idea/2023.2/feature_branch_diagram.png)



将分支合并到 master 是最常见的方法。

当您在功能分支中工作时，您的队友会继续将他们的工作提交给 master，这是很常见的情况：

![功能分支与主分支分离](https://intellijidea.com.cn/help/img/idea/2023.2/feature_branch_diverge_from_master_diagram.png)



当您运行时`merge`，功能分支中的更改将集成到目标分支的 HEAD 中：

![合并结果](https://intellijidea.com.cn/help/img/idea/2023.2/merge_result_diagram.png)

Git 创建一个新的提交 (M)，称为合并提交，它是从两个分支分歧点合并来自功能分支和主分支的更改而产生的。

> **合并分支**﻿
>
> 1. 在[“分支”](https://intellijidea.com.cn/help/idea/manage-branches.html)弹出窗口（主菜单Git | 分支）或 Git工具窗口的“分支”窗格中，选择要将更改集成到的目标分支，然后从上下文菜单中选择“签出”以切换到该分支。
>
> 2. 执行以下操作之一：
     >
     >    - 如果不需要指定合并选项，请选择要合并到当前分支的分支，然后从子菜单中选择“合并到当前”。
>
>    - 如果需要指定合并选项，请从主菜单中选择VCS Git | 合并更改以打开“合并”对话框：
       >
       >      > ![合并对话框](https://intellijidea.com.cn/help/img/idea/2023.2/merge_dialog.png)
       >      >
       >      > 选择要合并到当前分支的分支，单击“修改选项”并从以下选项中进行选择：
       >      >
       >      >     - `--no-ff`：在所有情况下都会创建合并提交，即使可以将合并解析为快进。
       >
       >      - `--ff-only`：只有可以快进时，合并才会被解决。
>      - `--squash`：将在当前分支之上创建包含所有拉取更改的单个提交。
>      - `-m`：您将能够编辑合并提交的消息。
>      - `--no-commit`：将执行合并，但不会创建合并提交，以便您可以在提交之前检查合并的结果。
     >
     >    单击“合并”。
>
> 如果你的工作树是干净的（这意味着你没有未提交的更改），并且你的功能分支和目标分支之间没有发生冲突，Git 将合并这两个分支，并且合并提交将出现在 Git 工具的 Log选项卡 中窗户 ：`Alt` `9`
>
> ![合并提交](https://intellijidea.com.cn/help/img/idea/2023.2/merge_commit.png)
>
> 如果您的分支与目标分支之间发生冲突，系统会提示您解决冲突（请参阅[解决冲突](https://intellijidea.com.cn/help/idea/resolve-conflicts.html)）。如果合并后仍有未解决的冲突，则“合并冲突”节点将出现在 “更改”视图的相应更改列表中，并提供解决这些冲突的链接。
>
> 如果您的本地更改将被合并覆盖，IntelliJ IDEA 将建议执行智能合并。如果您选择此选项，IntelliJ IDEA 将[存储](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#stash)未提交的更改，执行合并，然后取消存储更改。
>
> > 您可以通过从Git Branches弹出窗口中选择Abort操作来取消未完成的合并操作。



**2、变基分支 (git-rebase)**﻿

当您将`rebase`一个分支转移到另一个分支时，您可以将第一个分支的提交应用到第二个分支中的 HEAD 提交之上。

假设您创建了一个功能分支来处理特定任务并向该分支进行了多次提交：

![特征分支](https://intellijidea.com.cn/help/img/idea/2023.2/feature_branch_diagram.png)



当您在分支中开发时，您的队友会继续致力于掌握他们的工作：

![功能分支与主分支分离](https://intellijidea.com.cn/help/img/idea/2023.2/feature_branch_diverge_from_master_diagram.png)



当您执行操作时，您可以通过将您的提交应用到当前 HEAD 提交之上，将`rebase`您在功能分支中所做的更改集成到该分支中：`master``master`

![变基操作结果](https://intellijidea.com.cn/help/img/idea/2023.2/rebase_result_diagram.png)

> **将一个分支重新建立在另一个分支之上**﻿
>
> 1. 从主菜单中选择 Git | 变基：
     >
     >    ![Git 变基对话框](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_dialog.png)
>
> 2. 从列表中，选择要将当前分支变基到的目标分支：
     >
     >    ![在 Git rebase 对话框中选择目标分支](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_choose_target_branch_no_interactive.png)
>
>
>
> 3. 如果您需要从特定提交开始对源分支进行变基，而不是对整个分支进行变基，请单击修改选项并选择--onto。在源分支字段中，输入要将当前分支应用到新基础的提交的哈希值：
     >
     >    ![使用 --onto 指定提交哈希](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_specify_commit_no_interactive.png)
     >
     >    > ### 
     >    >
     >    >
     >    >
     >    > 要复制提交哈希，请在Log中选择它，右键单击它并选择Copy Revision Number。
>
> 4. 如果您要变基的分支当前未签出，请单击“修改选项”，单击“选择另一个要变基的分支”，然后从显示的列表中选择一个分支：
     >
     >    ![选择您想要变基的分支](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_choose_source_branch_no_interactive.png)
     >
     >    IntelliJ IDEA 将在开始变基操作之前检查此分支。
>
> 5. 如果要对分支中可访问的所有提交进行变基，请单击修改选项并选择--root（有关此选项的更多信息，请参阅[git-rebase](https://git-scm.com/docs/git-rebase)）。
>
> 6. 如果您需要保留空提交（即不会从其父级更改任何内容的提交），请单击修改选项并选择--keep-empty（有关此选项的更多信息，请参阅[git-rebase](https://git-scm.com/docs/git-rebase)）。
>
> 7. 如果您想在变基期间保留合并提交以便将它们保留在分支历史记录中，请单击“修改选项”并选择--preserve-merges（此选项对于`interactive`变基不可用）。
>
> 8. 单击变基。
>
> > 您可以通过从Git 分支弹出窗口顶部分别选择“中止”或“继续”操作来取消未完成的变基操作或恢复中断的变基操作。
>
> 如果不需要指定变基选项，则可以在不调用变基对话框的情况下启动变基。在“分支”弹出窗口或[Git](https://intellijidea.com.cn/help/idea/version-control-tool-window.html)工具窗口的[“分支”窗格](https://intellijidea.com.cn/help/idea/log-tab.html#branches_pane_context_menu)中，选择一个分支并选择以下操作之一：
>
>
>
> - 使用 Rebase （对于远程分支）拉入 Current以从所选分支中[获取更改，并在这些更改的基础上对当前分支进行变基。](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)
> - 检出并重新定基到当前（对于远程和本地分支）以检出所选分支并将其重新定基到当前检出的分支之上。如果远程分支本地不存在，IntelliJ IDEA 将静默创建一个跟踪的本地分支，检出并重新设置基准。
> - 将当前分支重新设置为所选分支（对于远程和本地分支）以将当前签出的分支重新设置为所选分支的基础。



**3、挑选单独的提交**﻿

有时，您只需要将单个提交应用到不同的分支，而不是变基或合并整个分支。这可能很有用，例如，如果您正在一个功能分支中工作，并且想要集成在两个分支分歧后提交的master 的修补程序。或者您可能想要将修复向后移植到以前的版本分支。您可以通过使用Cherry-pick操作来完成此操作。

挑选操作的状态显示在状态栏中。您始终可以通过在Git Branches弹出窗口中选择Abort Cherry-Pick来中止正在进行的 Cherry-Pick 。

![樱桃采摘作业状况](https://intellijidea.com.cn/help/img/idea/2023.2/cherry_pick_status.png)

> **将提交应用到另一个分支**﻿
>
> 1. 在[“分支”](https://intellijidea.com.cn/help/idea/manage-branches.html)弹出窗口（主菜单Git | Branches）中，选择要将更改集成到的目标分支，然后从弹出菜单中选择“签出”以切换到该分支。
>
> 2. 打开 Git工具窗口 并切换到“日志”选项卡。`Alt` `9`
>
> 3. 找到包含您要挑选的更改的提交。
     >
     >    您可以按分支、用户或日期过滤提交。您还可以单击![眼睛图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.inspectionsEye.svg)工具栏上的 并选择突出显示| 未选择的提交选项可将已应用于当前分支的提交灰显。如果您知道提交哈希，或者正在寻找标记的提交，您还可以使用“转到哈希/分支/标记”操作（按Git 工具窗口 的 “日志”选项卡，或单击工具栏上的 ）。Ctrl0FAlt09![搜索](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.find.svg)
>
> 4. 选择所需的提交。使用“提交详细信息”区域中的信息来确保这些是您想要传输到另一个分支的更改。
>
> 5. 单击工具栏上的择优挑选。 ![择优选择按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.icons.cherryPick.svg)IntelliJ IDEA 将应用更改并将更改提交到目标分支。
>
> 6. 如果挑选因冲突而失败，所选更改将显示在“更改”区域中，您可以在“更改”视图中看到 。您可以查看这些更改并在必要时稍后提交。
     >
     >    如果您希望 IntelliJ IDEA 在cherry-pick失败的情况下自动创建变更列表，请在“设置”|“设置”中打开相应的设置。版本控制 | 变更列表。
>
> 7. 将更改推送到目标分支。



**4、应用单独的更改**﻿

想象一下，您对一个文件进行了一些更改，并希望将其应用到不同的分支，但这些更改是与其他修改的文件一起提交的。IntelliJ IDEA 允许您应用单独的更改，而不是挑选整个提交。

> 1. 在[“分支”](https://intellijidea.com.cn/help/idea/manage-branches.html)弹出窗口（主菜单Git | Branches）中，选择要将更改集成到的目标分支，然后从弹出菜单中选择“签出”以切换到该分支。
>
> 2. 打开 Git工具窗口 并切换到“日志”选项卡。Alt09
>
> 3. 找到包含您要应用的更改的提交。
     >
     >    您可以按分支、用户或日期过滤提交。您还可以单击![眼睛图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.inspectionsEye.svg)工具栏上的 并选择突出显示| 未选择的提交选项可将已应用于当前分支的提交灰显。如果您知道提交哈希，或者正在寻找标记的提交，您还可以使用“转到哈希/分支/标记”操作（按Git 工具窗口 的 “日志”选项卡，或单击工具栏上的 ）。`Ctrl` `F` `Alt` `9` ![搜索](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.find.svg)
>
> 4. 在右侧的“提交详细信息”窗格中，选择包含要应用到目标分支的更改的文件，然后从上下文菜单中选择“Cherry-Pick Selected Changes” 。
>
> 5. 在打开的对话框中，选择现有变更列表或输入新变更列表的名称，然后单击“确定”。
>
> 6. 提交更改，然后将其推送到目标分支。



**5、应用单独的文件**﻿

除了对单个文件应用单独的更改之外，您还可以将整个文件的内容复制到不同的分支。例如，如果目标分支中不存在要应用的文件，或者在多次提交中对其进行了更改，这可能很有用。

> 1. [切换](https://intellijidea.com.cn/help/idea/manage-branches.html#switch-branches)到将应用更改的分支。
>
> 2. 在[“分支”](https://intellijidea.com.cn/help/idea/manage-branches.html)弹出窗口（主菜单Git | Branches）或 Git工具窗口的“分支”窗格中，选择包含要应用的文件的分支，然后从上下文菜单中选择“显示与工作树的差异” 。
     >
     >    打开的“更改”工具窗口显示所选分支中与当前签出的分支相比不同的所有文件的列表：
     >
     >    ![显示所选分支和当前工作树之间的差异](https://intellijidea.com.cn/help/img/idea/2023.2/ij_git_branches_diff.png)
     >
     >    - 所选分支中存在且当前分支中缺失的文件标记为灰色。
>    - 当前分支中存在但所选分支中缺失的文件标记为绿色。
>    - 包含所选分支和当前分支之间差异的文件用蓝色标记。
     >
     >    您可以单击“交换分支”链接来更改将哪个分支视为与其他分支进行比较的基础。
>
> 3. 选择要应用到当前分支的文件，然后从上下文菜单中选择“从分支获取”![从分行获取](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.download.svg)或单击工具栏上的 。
>
> 4. 提交并推动更改。IntelliJ IDEA 会将文件的全部内容复制到当前分支。
>
> > 您还可以从“项目”视图将文件应用到另一个分支：选择包含要复制的文件的文件夹，然后选择“Git |”。与分支比较| 从上下文菜单中选择<branch_name> ，然后单击工具栏上的“获取”图标。![得到](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.download.svg)



## 解决 Git 冲突

当您在团队中工作时，您可能会遇到有人将更改推送到您当前正在处理的文件的情况。如果这些更改不重叠（即，对不同的代码行进行了更改），则会自动合并冲突的文件。但是，如果相同的行受到影响，Git 无法随机选择一侧而不是另一侧，并要求您解决冲突。

在 Git 中，当您尝试执行以下操作之一时可能会出现冲突：[pull](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#pull)、[merge](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)、[rebase](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)、[cherry-pick](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#cherry-pick)、[unstash 更改](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#unstash)或[apply a patch](https://intellijidea.com.cn/help/idea/using-patches.html#apply-patch)。如果存在冲突，这些操作将失败，并且系统将提示您接受上游版本、首选您的版本或合并更改：

![合并冲突的文件对话框](https://intellijidea.com.cn/help/img/idea/2023.2/merge_conflicts_dialog.png)

当在 Git 级别检测到冲突时，会自动触发“冲突”对话框。

如果您在此对话框中单击“关闭”或从命令行调用导致合并冲突的 Git 操作，则“本地更改”视图中将出现“合并冲突”节点，并提供用于解决这些问题的链接：

![本地更改视图中的合并冲突节点](https://intellijidea.com.cn/help/img/idea/2023.2/git_merge_conflicts_node.png)

IntelliJ IDEA 提供了一个在本地解决冲突的工具。该工具由三个窗格组成：

- 左侧窗格显示只读本地副本
- 右窗格显示签入存储库的只读版本。
- 中央窗格是一个功能齐全的编辑器，其中显示解决冲突的结果。最初，此窗格的内容与文件的基本修订版本相同，即派生两个冲突版本的修订版本。

![冲突解决工具中的颜色编码](https://intellijidea.com.cn/help/img/idea/2023.2/conflict_resolution_tool_legend.png)



> **解决冲突**﻿
>
> 1. 单击“冲突”对话框中的“合并”、“本地更改”视图中的“解决”链接，或在编辑器中选择冲突文件并选择“VCS | ”。git | git 从主菜单解决冲突。
>
> 2. 要自动合并所有不冲突的更改，请单击工具栏上的![应用不冲突的更改按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.applyNotConflicts.svg)(应用所有不冲突的更改)。您还可以使用![从左侧应用不冲突的更改按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.applyNotConflictsLeft.svg)（从左侧应用非冲突更改）和![从右侧按钮应用不冲突的更改](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.applyNotConflictsRight.svg)（从右侧应用非冲突更改）分别合并对话框左/右部分的非冲突更改。
>
> 3. 要解决冲突，您需要选择对左侧（本地）和右侧（存储库）版本应用哪个操作（接受![接受按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.arrow.svg)或忽略），并在中央窗格中检查生成的代码：![忽略按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.remove.svg)
     >
     >    ![解决冲突](https://intellijidea.com.cn/help/img/idea/2023.2/resolveConflict.png)
     >
     >    您还可以右键单击中央窗格中突出显示的冲突，然后使用上下文菜单中的命令。使用左侧解决和使用右侧解决命令分别提供了从一侧接受更改并从另一侧忽略更改的快捷方式：
     >
     >    ![冲突更改的上下文菜单](https://intellijidea.com.cn/help/img/idea/2023.2/resolve_using_left_right.png)
     >
     >    对于简单冲突（例如，如果同一行的开头和结尾已在不同的文件修订版中修改），可以使用“解决简单冲突” ![解决简单冲突按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.magicResolve.svg)按钮，该按钮允许一键合并更改。
     >
     >    ![解决简单冲突按钮](https://intellijidea.com.cn/help/img/idea/2023.2/simple_conflict_resolve.png)
     >
     >    此类冲突无法通过“应用所有非冲突更改”操作来解决，因为您必须确保它们得到正确解决。
     >
     >    > ### 
     >    >
     >    >
     >    >
     >    > 请注意，中央窗格是一个功能齐全的编辑器，因此您可以直接在此对话框中更改结果代码。
>
> 4. 比较不同版本以解决冲突也可能很有用。使用![比较内容按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)工具栏按钮调用选项列表。请注意，Base是指本地版本和存储库版本源自的文件版本（最初显示在中间窗格中），而Middle是指结果版本。
>
> 5. 在中央窗格中查看合并结果，然后单击“应用”。



**1、生产力技巧**﻿

> 自动应用不冲突的更改
>
> 您可以将 IntelliJ IDEA 配置为始终自动应用不冲突的更改，而不是从“合并”对话框中告诉它这样做。为此，请选择“工具”| “自动应用不冲突的更改”选项。IDE 设置的 Diff Merge页面。`Ctrl` `Alt` `S`

> 在中央窗格中管理更改
>
> 您可以使用将鼠标悬停在装订线中的更改标记上然后单击它时出现的工具栏来管理中央窗格中的更改。工具栏与一个框架一起显示，该框架显示修改行的先前内容：
>
> ![更改工具栏](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts_change_toolbar.png)
>
> 例如，当存在多个不冲突的更改时，您只需跳过其中一两个更改，则可以更轻松地使用“应用所有不冲突的更改”操作同时应用所有更改，然后使用“还原”撤消不需要的更改。从此工具栏执行操作。



**2、处理与 LF 和 CRLF 行结尾相关的冲突**﻿

通常，在团队中工作并为同一存储库做出贡献的人们使用不同的操作系统。这可能会导致行结束问题，因为 Unix、Linux 和 macOS 使用`LF`，而 Windows 使用`CRLF`来标记行结束。

IntelliJ IDEA 在差异查看器中显示行结尾的差异，以便您可以手动修复它们。如果您希望 Git 自动解决此类冲突，则需要在 Windows 上将该`core.autocrlf`属性设置为to ，在 Linux 和 macOS 上则需要将该属性设置为 to（更多详细信息，请参阅[处理行结尾](https://help.github.com/articles/dealing-with-line-endings/)）。您可以通过在 Windows 或Linux 和 macOS 上运行来手动更改配置。`true``input``git config --global core.autocrlf true``git config --global core.autocrlf input`

但是，IntelliJ IDEA 可以自动分析您的配置，在您要提交`CRLF`到远程存储库时发出警告，并建议将设置设置`core.autocrlf`为`true`或`input`取决于您的操作系统。

要启用对`LF`和`CRLF`行分隔符的智能处理，请打开“设置”对话框，然后选择“版本控制”|“版本控制”|“版本控制”。左侧的Git节点。启用“如果将要提交 CRLF 行分隔符则发出警告”选项。CtrlAlt0S

启用此选项后，每次您要提交带有分隔符的文件时， IntelliJ IDEA 都会显示行分隔符警告对话框，除非您在受影响的文件中`CRLF`设置了任何相关的[Git 属性](https://www.kernel.org/pub/software/scm/git/docs/gitattributes.html)（在这种情况下，IntelliJ IDEA 假设您清楚地了解您在做什么并从分析中排除该文件）。

在“行分隔符警告”对话框中，单击以下选项之一：

- 按原样提交忽略警告并提交带有`CRLF`分隔符的文件。
- 修复并提交以将`core.autocrlf`属性设置为`true`或`input`取决于您的操作系统。因此，行分隔符将在提交之前`CRLF`被替换。`LF`

如果稍后您需要查看合并过程中冲突的具体解决情况，可以在 Git工具窗口 的 “日志”选项卡中找到所需的合并提交，然后在右侧的“提交详细信息”窗格中选择有冲突的文件，然后单击或按。有关详细信息，请参阅[查看如何合并更改](https://intellijidea.com.cn/help/idea/investigate-changes.html#review_merge_commit)。`Alt` `9`![显示差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)`Ctrl` `D`





## 使用 Git 同时处理多个功能

有时，您需要在未完成的任务之间切换，然后再返回。IntelliJ IDEA 为您提供了几种方法来方便地处理多种不同的功能，而不会丢失您的工作：

- 您可以[隐藏](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#stash)或[搁置](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#shelve)待处理的更改。

  隐藏更改与搁置非常相似。唯一的区别在于补丁的生成和应用方式。存储由 Git 生成，可以从 IntelliJ IDEA 内部或外部应用。搁置更改的补丁由 IntelliJ IDEA 生成，也通过 IDE 应用。此外，存储涉及所有未提交的更改，而当您将更改放入搁置时，您可以选择一些本地更改，而不是搁置所有更改。

- 您可以[将与不同任务或功能相关的更改保留在不同的更改列表中](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#changelists)。

- 您可以创建[分支来处理不同的不相关功能](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#feature-branches)。



**1、搁置变更**﻿

搁置是暂时存储您尚未提交的待处理更改。例如，如果您需要切换到另一个任务，并且希望将更改放在一边以供稍后处理，则这非常有用。

使用 IntelliJ IDEA，您可以搁置单独的文件和整个变更列表。

> 您无法搁置未版本化的文件，即尚未[添加到版本控制的](https://intellijidea.com.cn/help/idea/adding-files-to-version-control.html#add-files-to-vcs)文件。

搁置后，可以根据需要多次应用更改。

> **搁置变更**﻿
>
> 1. 在 “提交”工具窗口中，右键单击要搁置的文件或更改列表，然后从上下文菜单中选择“搁置更改” 。`Alt` `0`
     >
     >    ![搁置变化](https://intellijidea.com.cn/help/img/idea/2023.2/shelve-changes.png)
>
> 2. 在“搁置更改”对话框中，查看已修改文件的列表。
>
> 3. 在“提交消息”字段中，输入要创建的架子的名称，然后单击“架子更改”按钮。
>
> 您还可以静默搁置更改，而不显示“搁置更改”对话框。为此，请选择要搁置的文件或更改列表，然后单击工具栏上的“静默搁置”图标或按。包含要搁置的更改的更改列表的名称将用作搁置名称。![默默搁置](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.shelveSilent.svg)`Ctrl` `Shift` `H`
>
> 为了避免出现多个同名的架子（例如Default），您可以将文件或更改列表从“提交到 <branch>”选项卡拖到“提交”工具窗口的“架子”选项卡，稍等片刻直到它被激活，释放鼠标按钮后编辑新的架子名称。
>
> > 如果您需要将更改复制到架子而不重置本地更改，请按并查找“保存到架子”操作。`Ctrl` `Shift` `A`

> **取消搁置变更**﻿
>
> 取消搁置是将推迟的更改从搁架移动到待处理的更改列表。未搁置的更改可以从视图中过滤掉或从搁置中删除。
>
> 1. 在[“搁置”](https://intellijidea.com.cn/help/idea/shelf-tab.html)选项卡中，选择更改列表或要取消搁置的文件。
>
> 2. 按或从所选内容的上下文菜单中选择“取消搁置” 。`Ctrl` `Shift` `U`
     >
     >    ![取消搁置变更](https://intellijidea.com.cn/help/img/idea/2023.2/py_unshelve_changes.png)
>
> 3. 在“取消搁置更改”对话框中，在“名称”字段中指定要将未搁置的更改恢复到的更改列表。您可以从列表中选择现有变更列表或输入要创建的新变更列表的名称。您可以在注释字段中输入新变更列表的描述（可选）。
     >
     >    如果您想让新的更改列表处于活动状态，请选择“设置活动”。否则，当前活动变更列表保持活动状态。
>
> 4. 如果您希望 IntelliJ IDEA 在停用时保存与新变更列表关联的任务的上下文，并在变更列表变为活动状态时恢复上下文，请选择“跟踪上下文”选项（有关详细信息，请参阅[任务和上下文）。](https://intellijidea.com.cn/help/idea/managing-tasks-and-context.html)
>
> 5. 如果要删除要取消搁置的更改，请选择“从搁置中删除已成功应用的文件”选项。未搁置的文件将从该搁置中删除，添加到另一个更改列表中，并标记为已应用。![删除图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.gc.svg)只有通过单击工具栏上的 或从上下文菜单中选择清理已取消搁置来明确删除它们，它们才会被完全删除。
     >
     >    > 如果您意外删除了未搁置的文件，您可以从“最近删除”节点查看和恢复它们。
>
> 6. 单击“确定”。如果修补版本与当前版本发生冲突，请按照[解决冲突](https://intellijidea.com.cn/help/idea/resolving-conflicts.html)中的说明进行解决。
>
> 您还可以静默取消搁置更改，而不显示“取消搁置更改”对话框。为此，请选择要取消搁置的文件或更改列表，然后单击工具栏上的“静默取消搁置”图标或按。未搁置的文件将移至活动的挂起更改列表。![默默取消搁置图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.unshelveSilent.svg)`Ctrl` `Alt` `U`
>
> 您还可以将文件或更改列表从“搁置”选项卡拖到“提交到 <branch>”选项卡以静默取消搁置。如果按住键拖动它，它将被复制到“提交到分支”选项卡，但也会保留在架子中。`Ctrl`

> **放弃搁置的更改**﻿
>
> 1. 在“书架”视图中，选择包含您不想再保留的更改的更改列表。
> 2. 右键单击更改列表，然后从上下文菜单中选择“删除”或按。`Delete`

> **恢复未搁置的更改**﻿
>
> IntelliJ IDEA 允许您在必要时重新应用未搁置的更改。所有未搁置的更改都可以重复使用，直到通过单击![删除未搁置的更改](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.gc.svg)工具栏上的图标或从上下文菜单中选择“清理已未搁置”来明确删除它们为止。
>
> 1. 确保已启用显示已取消搁置的工具栏选项。 ![显示已下架按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.patch_applied.svg)
> 2. 选择要恢复的文件或架子。
> 3. 从所选内容的上下文菜单中，选择“恢复”。

> **应用外部补丁**﻿
>
> 您可以导入在 IntelliJ IDEA 内部或外部创建的补丁，并将它们作为搁置的更改应用。
>
> 1. 在Shelf视图中，从上下文菜单中选择Import Patches 。
> 2. 在打开的对话框中，选择要应用的补丁文件。选定的补丁将在“Shelf”选项卡中显示为“shelf”。
> 3. 选择新添加的带有补丁的架子，然后从所选内容的上下文菜单中选择“取消搁置更改” 。

> **自动搁置基础修订**﻿
>
> 将 IntelliJ IDEA 配置为始终搁置受 Git 版本控制的文件的基本修订版本可能很有用。
>
> 1. 按打开 IDE 设置，然后选择版本控制 | 架子。`Ctrl` `Alt` `S`
>
> 2. 选择“在分布式版本控制系统下搁置文件的基本修订版本”选项。
     >
     >    如果启用此选项，文件的基本修订版本将保存到架子上，如果应用架子导致冲突，则该架子将在[三向合并](https://en.wikipedia.org/wiki/Merge_(version_control)#Three-way_merge)期间使用。如果禁用，IntelliJ IDEA 将在项目历史记录中查找基础修订版，这可能需要一段时间；此外，冲突架所基于的修订可能会丢失（例如，如果历史记录因变基操作而更改）。

> **更改默认架子位置**﻿
>
> 默认情况下，shelf 目录位于您的项目目录下。但是，您可能想要更改默认的架子位置。例如，如果您想避免在清理工作副本时意外删除架子，或者希望将它们存储在单独的存储库中，以便在团队成员之间共享架子，这可能很有用。
>
> 1. 按打开 IDE 设置，然后选择版本控制 | 架子。`Ctrl` `Alt` `S`
> 2. 单击更改书架位置并在打开的对话框中指定新位置。
> 3. 如有必要，选择将架子移动到新位置以将现有架子移动到新目录。



**2、隐藏更改**﻿

有时可能需要恢复工作副本以匹配 HEAD 提交，但您不想丢失已经完成的工作。如果您了解到存在可能与您正在做的事情相关的上游更改，或者您需要进行一些紧急修复，则可能会发生这种情况。

存储涉及记录 HEAD 提交和工作目录当前状态（存储）之间的差异。对索引的更改也可以被隐藏。

取消存储涉及将存储的存储应用到分支。

您可以将存储应用到现有分支或在其基础上创建新分支。

存储可以根据需要多次应用到您需要的任何分支，只需[切换到所需的分支](https://intellijidea.com.cn/help/idea/manage-branches.html#switch-branches)即可。请记住：

- 在一系列提交后应用存储会导致需要解决的冲突。
- 您不能将存储应用到“脏”工作副本，即具有未提交更改的工作副本。

> **将更改保存到存储中**﻿
>
> 1. 转到 Git | 未提交的更改 | 隐藏更改。
> 2. 在打开的“存储”对话框中，选择适当的 Git 根目录并确保签出正确的分支。
> 3. 在“消息”字段中描述您要存储的更改。
> 4. 要存储本地更改并将索引中暂存的更改引入工作树以进行检查和测试，请选择“保留索引”选项。
> 5. 单击创建存储。

> **应用隐藏**﻿
>
> 1. 转到 Git | 未提交的更改 | 取消隐藏更改。
>
> 2. 选择要应用存储的 Git 根目录，并确保签出正确的分支。
>
> 3. 从列表中选择您想要应用的存储。
     >
     >    如果您想检查所选存储中哪些文件受到影响，请单击“查看”。
>
> 4. 要在应用所选存储后将其删除，请选择“弹出存储”选项。
>
> 5. 要同时应用隐藏的索引修改，请选择“恢复索引”选项。
>
> 6. 如果您想基于所选存储创建新分支，而不是将其应用到当前签出的分支，请在作为新分支字段中输入该分支的名称。
>
> 要删除存储，请在列表中选择它，然后单击“删除”。要删除所有隐藏内容，请单击“清除”。



**3、将更改分组到不同的更改列表中**﻿

当您正在开发多个相关功能时，您可能会发现将更改分组到不同的[更改列表](https://intellijidea.com.cn/help/idea/managing-changelists.html)中很方便。与使用[功能分支](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#feature-branches)来处理多个任务相比，这种方法有其优点和缺点。

优点：

- 您可以轻松地在不同的逻辑更改集之间切换，并分别提交它们。
- 与出于相同目的使用分支不同，您可以随时进行所有更改，而无需在分支之间切换，如果您的项目非常大，这可能需要一段时间。
- 测试不同功能如何协同工作很方便。
- 您可以在构建服务器上远程运行更改列表。

缺点：

- 虽然与分支相比，使用更改列表似乎是一个更轻量级的选项，但它并不安全，因为在提交并推送更改之前，没有更改的备份。如果您的本地工作副本发生问题，您的所有更改都将丢失，因为它们不属于 Git 项目历史记录。
- 不可能对功能进行原子测试。
- 不可能就同一功能进行协作。此外，除非您通过电子邮件发送包含更改的补丁，否则您无法从不同的计算机进行贡献，这可能不是很方便。



所有更改列表都显示在 “提交到 <branch>”选项卡的“更改”视图中。所有修改的文件都会自动放置在活动变更列表中，即“更改”变更列表，除非您创建了不同的变更列表并将其激活。

更改列表显示在 “更改”视图中。最初，有一个名为Changes的默认更改列表。所有新更改都会自动放入更改更改列表中。还有一个未版本控制的文件更改列表，用于对尚未[添加到 VCS 中的](https://intellijidea.com.cn/help/idea/adding-files-to-version-control.html#add-files-to-vcs)新创建的文件进行分组。

![提交工具窗口中的更改列表](https://intellijidea.com.cn/help/img/idea/2023.2/changelists_in_commit_tw.png)

您可以根据需要[创建任意数量的更改列表](https://intellijidea.com.cn/help/idea/managing-changelists.html#new_changelist)，并随时[使其中任何一个更改列表处于活动状态。](https://intellijidea.com.cn/help/idea/managing-changelists.html#active-changelist)您可以[将](https://intellijidea.com.cn/help/idea/managing-changelists.html#move-between-changelists)任何未提交的更改移至任何更改列表。

> **创建新的变更列表**﻿
>
> 1. 在“本地更改”视图中，单击![更改列表图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.changelist.svg)工具栏上的 并选择“新建更改列表”。
> 2. 在“新建更改列表”对话框中，指定新更改列表的名称，并添加说明（可选）。

> **设置活动变更列表**﻿
>
> - 在“本地更改”视图中，选择一个非活动更改列表，然后按或右键单击它，然后从上下文菜单中选择“设置活动更改列表” 。所有新的更改都会自动放入此更改列表中。`Ctrl` `Space`

> ### 在更改列表之间移动更改﻿
>
> 1. 在“本地更改”视图中，选择要移动到另一个更改列表的更改。
> 2. 右键单击所选内容或单击![更改列表图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.changelist.svg)工具栏上的 并选择“移动到另一个更改列表” 。`Alt` `Shift` `M`
> 3. 在打开的对话框中，选择现有变更列表或输入新变更列表的名称。
> 4. 您可以选择使目标更改列表处于活动状态并跟踪其上下文（IntelliJ IDEA 将保存与此更改列表关联的上下文，并在该更改列表变为活动状态时恢复它）。
>
> > 您还可以在更改列表之间拖动文件。
>
> > 有关将一个文件中的更改放入 Git 中的不同更改列表的更多信息，请参阅将[更改放入不同的更改列表](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#put_changes_into_different_changelists)。

> **删除变更列表**﻿
>
> - 右键单击更改列表，然后从上下文菜单中选择“删除更改列表” 。



**4、使用功能分支**﻿

Git 中的分支代表独立的开发线，因此，如果您正在开发一个单独的功能，并且希望在准备好共享工作结果并将其集成到 中之前完成并测试该功能，那么在功能分支中执行此操作`master`是最好的解决方案。通过这种方式，您可以确保不稳定的代码不会提交到项目的主代码库，并且如果需要，您可以轻松切换到其他任务。

优点：

- 与使用变更列表对变更进行分组相反，使用功能分支是安全的。在您向 Git 提交更改后，它们将成为 Git 项目历史记录的一部分，因此即使您损坏了工作树，您也始终可以通过[Git reflog](https://git-scm.com/docs/git-reflog)恢复您的提交。推送更改后，它们就会被备份。
- 您可以开发并行的不相关功能并以原子方式测试它们。
- 当您完成分支中的开发后，您可以[重新排序或压缩提交](https://intellijidea.com.cn/help/idea/edit-project-history.html#interactive-rebase)，以便您的历史记录是线性且干净的。
- 可以轻松地就您的功能进行协作，或者从不同的机器上进行开发。

缺点：

- 在非常大的项目上切换分支可能需要时间。
- 一起测试相关功能不太方便。
- 您必须学习[使用功能分支](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#feature-branches)并将更改集成到主代码库中的工作流程。

使用功能分支并将更改集成到主代码库中有两种主要方法：

- [合并](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#merge-option)选项
- [变基](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#rebase-option)选项

**①、使用合并来集成功能分支中的更改**﻿

合并选项的主要好处是完全可追溯性，因为合并到主代码库中的提交保留了其原始哈希值和作者，并且属于一项功能的所有提交都可以分组在一起。

此工作流程适用于向主代码库提交更改涉及[拉取请求](https://intellijidea.com.cn/help/idea/work-with-github-pull-requests.html#create-pull-request)或分层审批程序的项目，因为现有分支不会以任何方式更改。

这种方法的主要缺点是，每次需要合并更改时都会创建无关的合并提交，这会严重污染项目历史记录并使其难以阅读。

> 1. 为您单独的开发线[创建一个分支。](https://intellijidea.com.cn/help/idea/manage-branches.html#create-branch)
> 2. [在开发时提交](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#commit)更改。
> 3. [将您的分支推](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html)送到远程存储库。这样做是为了备份，以便您可以在不同的计算机上进行协作或工作。
> 4. 当您需要执行与您的功能无关的工作时，请切换到不同的分支。
> 5. 对您的功能进行审查和测试，并进行必要的修复。
> 6. 当您准备好将工作结果集成到主分支中时（例如`master`），请执行以下操作：
     >    1. [将](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)您的功能分支合并到主代码库中。
>    2. [删除功能分支](https://intellijidea.com.cn/help/idea/manage-branches.html#delete-branch)。
>    3. 推。



**②、使用 rebase 集成功能分支中的更改**﻿

此选项的主要好处是您可以获得清晰的项目历史记录，易于其他人阅读和理解。您的日志不包含操作产生的不必要的合并提交`merge`，并且您可以获得易于导航和搜索的线性历史记录。

然而，当决定采用此工作流程时，您应该记住，这会`rebase`重写项目历史记录，因为它会为原始功能分支中的每个提交创建新的提交，因此它们将具有不同的哈希值，这会阻碍可追溯性。

> 1. 为您单独的开发线[创建一个分支。](https://intellijidea.com.cn/help/idea/manage-branches.html#create-branch)
>
> 2. [在开发过程中经常提交](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#commit)更改。
>
> 3. [将您的分支推](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html)送到远程存储库。这样做是为了备份，以便您可以在不同的计算机上进行协作或工作。
>
> 4. `master`时不时地[重新调整](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)你的功能分支。仅当您的功能分支很长时才有意义。这对于：
     >
     >    - 确保你的功能分支`master`不会相距太远。
>    - 当您最终将更改集成到主代码库中时，避免解决大量冲突。当您定期进行变基时，您可以迭代地解决冲突，并且不会最终因长期差异而苦苦挣扎。
>    - 加快检查分支的速度，因为一旦分支足够分散，分支之间的切换就会变慢。
     >
     >    变基涉及以下步骤：
     >
     >    1. 从远程[获取](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)更改，或将更改[拉](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#pull)`master`入分支。
>    2. 将您的分支[重新定位](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)`master`到.
>    3. [强制将](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#force-push)操作结果推`rebase`送到您的功能分支。
>
> 5. `master`当您需要执行与您的功能无关的工作时切换到。当您返回到功能分支时，执行Checkout 并 Rebase 到 Current。
>
> 6. 对您的功能进行审查和测试，并进行必要的修复。
>
> 7. 当您的功能完成后，执行交互式变基。这允许您[重新排序和压缩](https://intellijidea.com.cn/help/idea/edit-project-history.html#interactive-rebase)提交，以使您的功能分支历史记录看起来干净整洁。
>
> 8. 当您准备好将工作结果集成到主分支中时（例如`master`），请执行以下操作：
     >
     >    1. [去](https://intellijidea.com.cn/help/idea/manage-branches.html#checkout-branch)分行看看`master`吧
>    2. [将](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)您的分支与`master`. 由于`master`没有分歧，Git 只会将指针向前移动到功能分支的最新提交，而不是创建新的合并提交（这称为快进合并）。
>    3. [删除功能分支](https://intellijidea.com.cn/help/idea/manage-branches.html#delete-branch)。
>    4. [推](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html)。
>
> 使用您的姓名缩写或昵称（如果很短）作为功能分支名称的前缀是有意义的。这样，您始终可以使用“分支机构”菜单中的快速搜索轻松找到所有分支机构。



## 撤消 Git 存储库中的更改

> **恢复未提交的更改**﻿
>
> 在提交之前，您始终可以在本地撤消所做的更改：
>
> - 在 “提交”工具窗口中，选择一个或多个要还原的文件，然后从上下文菜单中选择“回滚” ，或按。`Alt` `0` `Ctrl` `Alt` `Z`
>
> 自上次提交以来对所选文件所做的所有更改都将被丢弃，并且它们将从活动更改列表中消失。

> **取消暂存文件**﻿
>
> 默认情况下，IntelliJ IDEA 使用[更改列表](https://intellijidea.com.cn/help/idea/managing-changelists.html)概念，其中修改的文件会自动暂存。
>
> - 如果文件已处于版本控制之下，并且您不想提交它，您可以：
    >   - [从提交中删除它](https://intellijidea.com.cn/help/idea/adding-files-to-version-control.html)：不要在提交工具窗口的更改区域中选择它。
>   - [将其移至另一个变更列表](https://intellijidea.com.cn/help/idea/managing-changelists.html#move-between-changelists)。
> - 如果您更习惯暂存概念，请选择版本控制 |中的启用暂存区域选项。IDE 设置的 Git页面。`Ctrl` `Alt` `S`
>
> 此外，默认情况下 IntelliJ IDEA 建议将每个新创建的文件添加到版本控制下。您可以在“设置”|“设置”中更改此行为。版本控制 | 分别使用“创建文件时”和“删除文件时”设置进行确认。

> **撤消最后一次提交**﻿
>
> IntelliJ IDEA 允许您撤消当前分支中的最后一次提交。
>
> > 如果提交被推送到受保护的分支，则无法撤消该提交，即不允许使用[强制 --push](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#force-push)的分支（在IDE 设置的 版本控制 | Git页面中配置受保护的分支）请注意，如果分支被标记由于 GitHub 上受保护，当您签出时，IntelliJ IDEA 会自动将其标记为受保护。`Ctrl` `Alt` `S`
>
> 1. 打开 Git工具窗口 并切换到“日志”选项卡。`Alt` `9`
> 2. 选择当前分支中的最后一次提交，然后从上下文菜单中选择“撤消提交” 。
> 3. 在打开的对话框中，选择一个更改列表，您要放弃的更改将移至其中。您可以从名称列表中选择现有变更列表，也可以指定新变更列表的名称（默认情况下使用提交消息）。
> 4. 如果您想要使用要放弃活动更改列表的更改来创建更改列表，请选择“设置活动”选项。
> 5. 如果您希望 IntelliJ IDEA 记住您的上下文并在此更改列表变为活动状态时重新加载编辑器中当前打开的文件，请选择“跟踪上下文”选项。

> **恢复推送的提交**﻿
>
> 如果您发现已推送的特定提交中有错误，您可以恢复该提交。此操作会产生一个新的提交，该提交会逆转您要撤消的提交的效果。因此，项目历史记录被保留，因为原始提交保持不变。
>
> 1. 在Git工具窗口 的 “日志”选项卡中找到要还原的提交 ，右键单击它并从上下文菜单中选择“还原提交” 。也可以从文件[历史记录](https://intellijidea.com.cn/help/idea/version-control-tool-window-history-tab.html)视图中提交的上下文菜单中使用此选项。“提交更改”对话框将打开，其中包含自动生成的提交消息。`Alt` `9`
     >
     >    > 如果将此操作应用于“日志”视图中选择的多个提交，则会创建一个单独的提交来还原每个提交。
>
> 2. 如果所选提交包含多个文件，并且您只需要恢复其中一些文件，请取消选择您不想触及的文件。
>
> 3. 单击“提交”以提交更改集，该更改集将还原对此特定提交中所选文件的更改。

> **恢复选定的更改**﻿
>
> 如果此提交包含多个文件并且您只需要恢复其中一些文件，则 IntelliJ IDEA 允许您撤消推送提交中选定的更改。
>
> 1. 在日志视图中，选择包含要放弃的更改的提交。
>
> 2. 在[“更改的文件”](https://intellijidea.com.cn/help/idea/log-tab.html#changedFiles)窗格中，右键单击要还原的文件，然后从上下文菜单中选择“还原选定的更改” 。
     >
     >    这会产生一个新的提交，该提交会撤销您想要撤消的更改。

> **删除提交**﻿
>
> 与反映在分支历史记录中的[恢复提交](https://intellijidea.com.cn/help/idea/undo-changes.html#revert-commit)不同，您可以丢弃当前分支中推送的提交，而不会留下任何操作痕迹。
>
> > [与任何重写分支](https://intellijidea.com.cn/help/idea/edit-project-history.html)历史记录的操作一样，删除提交需要[--force 推送](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#force-push)，并且不能在受保护的分支中执行（这些可以在IDE 设置的 版本控制 | Git页面中进行配置）。`Ctrl` `Alt` `S`
>
> - 在日志视图中选择要放弃的提交，然后从上下文菜单中选择“删除提交” 。

> **将分支重置为特定提交**﻿
>
> 如果您发现最近的一组提交中存在错误并想要重做该部分，则可以将存储库回滚到特定状态。这是通过将当前分支 HEAD 重置为指定的提交来完成的（如果您不想在历史记录中反映撤消，则可以选择重置索引和工作树）。
>
> 1. 打开 版本控制工具窗口 并切换到日志选项卡。Alt09
> 2. 选择要将 HEAD 移至的提交，然后从上下文菜单中选择将当前分支重置到此处。
> 3. 在打开的Git Reset对话框中，选择您希望如何更新工作树和索引，然后单击Reset：
     >    - Soft：所选提交之后所做的所有更改都将暂存（这意味着它们将被移动到“ 更改”视图，以便您可以查看它们并在必要时稍后提交）。
>    - 混合：将保留所选提交后所做的更改，但不会暂存提交。
>    - Hard：所选提交后所做的所有更改都将被丢弃（暂存和提交）。
>    - Keep：所选提交后所做的已提交更改将被丢弃，但本地更改将保持不变。

> **获取文件的先前修订版本**﻿
>
> 如果您需要恢复单个文件而不是丢弃包含对多个文件的更改的整个提交，您可以返回到该文件的特定版本：
>
> 1. 在任何视图（项目工具窗口、编辑器、 更改视图等）中选择必要的文件。
> 2. 选择Git | 从VCS主菜单或选择的上下文菜单显示历史记录。“历史记录”选项卡已添加到 Git工具窗口，显示所选文件的历史记录，并允许您查看和比较其修订版本。
> 3. 确定要回滚到的修订版本后，在列表中选择它，然后从上下文菜单中选择“获取” 。



## 使用标签来标记特定的 Git 提交﻿

Git 允许您将标签附加到提交中，以标记项目历史记录中的某些点，以便您将来可以引用它们。例如，您可以标记与发布版本相对应的提交，而不是创建路径来捕获发布[快照](https://intellijidea.com.cn/help/idea/manage-branches.html#create-branch)。

> **为提交分配标签**﻿
>
> 1. 打开 Git工具窗口 并切换到“日志”选项卡。Alt09
>
> 2. 找到所需的提交，右键单击它并从上面菜单中的“新建标签”。
>
> 3. 输入新标签的名称并单击“确定”。该标签将显示在 Git工具窗口 的 “日志”选项卡中：Alt09
     >
     >    ![标记提交](https://intellijidea.com.cn/help/img/idea/2023.2/tagged_commit.png)

> **将带注释的标签分配给提交**﻿
>
> 带注释标签的元数据包含创建用户的名称，因此允许您检查谁放置了它们。
>
> 1. 转到Git |新标签。
> 2. 在打开的“标签”对话框中，在“Git Root”下，选择要在其中标记提交的本地存储库的路径，并指定新标签的名称。
> 3. 在“提交”字段中，指定要标记的提交。您可以输入提交哈希值，或使用表达式，例如：`<branch>~<number of commits backwards between the latest commit (HEAD) and the required commit>`。有关更多信息，请参阅 Git[提交命名约定](http://www.kernel.org/pub/software/scm/git/docs/user-manual.html#naming-commits)。
> 4. 在消息字段中输入一些注释以创建带注释的标签（如果为空，则将创建常规标签）。
> 5. 点击“创建标签”。
>
> > 如果在“日志”工具栏的“快速设置”下启用“简洁引用视图”选项，则标记名称将隐藏在分支名称后面并且不可见。
>
> > 如果您不需要指定任何其他选项，还可以右键单击版本控制工具窗口的“日志”选项卡 中的提交 ，然后从上下文菜单中选择“新建标签”。`Alt` `9`

> **分配重新现有标签**﻿
>
> 如果您在错误的提交上放置了标签，并且想要重新分配它（例如，指示发布版本的提交），请执行以下操作：
>
> 1. 转到Git |新标签。
> 2. 在“标签”对话框的“标签名称”字段中指定要重新分配的现有标签的名称。
> 3. 选择强制选项。
> 4. 在提交字段中，指定标签移动到提交位置，然后单击创建标签。

> **跳转到标记的工作**﻿
>
> 1. 打开 Git工具窗口 并切换到“日志”选项卡。`Alt` `9`
>
> 2. 单击工具栏上的“转到分区/分支/标签”图标，或按。![应用程序操作文件夹](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.find.svg)`Ctrl` `F`
     >
     >    ![转移分区/分支/标签图标](https://intellijidea.com.cn/help/img/idea/2023.2/go_to_hash.png)
>
> 3. 输入标签名称（[代码完成会](https://intellijidea.com.cn/help/idea/auto-completing-code.html)在您键入时建议标签名称）并按。`Enter`

> **查看标记的提交**﻿
>
> 假设您使用标签标记了与发布版本相对应的作业，现在您想要查看项目在该时间点的快照。您可以通过检查标记的作业来实现这一点。执行以下操作之一：
>
> - [找到](https://intellijidea.com.cn/help/idea/use-tags-to-mark-specific-commits.html#jump-to-tag)要签出的标记提交，右键单击它并从上下文菜单中选择“签出修订”。
> - [调用分支弹出窗口](https://intellijidea.com.cn/help/idea/manage-branches.html#invoke-branches-popup)，单击“签出标签”或“修订版本”，然后输入标签名称（IntelliJ IDEA 在您输入时提供匹配标签和修订版本的列表）。
>
> 请注意，此操作会导致[分离的 HEAD](https://git-scm.com/docs/git-checkout#_detached_head)，这意味着您不再位于任何分支中。您可以使用此快照进行检查和实验。但是，如果您想在此快照上面提交更改，则需要[创建一个分支](https://intellijidea.com.cn/help/idea/manage-branches.html#create-branch)。

> **积极标签**﻿
>
> 默认情况下，当您执行`push`操作时，标签不会发送到远程存储库。
>
> 1. 在“积极作业”活动中，选中左下角的“积极活动标签”。
     >
     >    ![“作业活跃”对话框中的“活跃标签”选项](https://intellijidea.com.cn/help/img/idea/2023.2/push_tags.png)
>
> 2. 在下拉菜单中，选择您要锻炼的标签：
     >
     >    - 如果您想要人群的所有标签，包括不属于您想要的人群的选定主题的标签，请选择“全部”（第三方）`push --tags`。
>    - 如果您的人群属于您要人群的选定分支的标签，请选择当前`push --follow-tags`路径（路径）。
>
> 3. 单击“全民”。

> **删除标签**﻿
>
> - [找到](https://intellijidea.com.cn/help/idea/use-tags-to-mark-specific-commits.html#jump-to-tag)标记的提交，右键单击它并选择标记 <tag_name> |从上下文菜单中删除。



## 编辑 Git 项目历史记录

Git 允许您编辑项目历史记录。当您正在处理功能分支并希望在与其他人[共享](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html)之前清理它并使其看起来像您想要的方式时，这非常有用。例如，您可以编辑提交消息，将与相同功能相关的较小提交压缩在一起，或者将包含不相关更改的提交拆分为单独的提交，将更改添加到先前的提交等。

> 除非绝对必要，否则请避免修改具有多个贡献者的远程分支的历史记录，例如，如果您不小心推送了一些敏感数据。
>
> 为了防止数据丢失，将拒绝将重写分支历史记录的修改推送到远程存储库，因此您必须强制[推送](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#force-push)更改。
>
> 您无法在不允许的情况下修改受保护分支的历史记录（在IDE 设置的 版本控制 | Git页面中配置受保护分支）。请注意，如果分支在 GitHub 上标记为受保护，则 IntelliJ IDEA 会在您修改时自动将其标记为受保护。一探究竟。`push --force``Ctrl` `Alt` `S`
>
> 此外，您无法执行修改当前签出分支中未包含的提交的分支历史记录的操作。

**1、编辑提交消息**﻿

如果您唯一需要更改的是提交消息，则可以在推送此提交之前对其进行编辑。

> 1. 在Git工具窗口 的“日志”选项卡 中右键单击要编辑其消息的提交 ，然后从上下文菜单中选择“编辑提交消息” ，或按。`Alt` `9` `F2`
> 2. 在打开的对话框中，输入新的提交消息并单击“确定”。

**2、修改之前的commit**﻿

有时，您可能会过早提交并忘记添加一些文件，或者注意到上次提交中存在错误，您希望在不创建单独提交的情况下修复该错误。

您可以通过使用“修改提交”选项来执行此操作，该选项将分阶段更改附加到先前的提交。因此，您最终会得到一次提交，而不是两次不同的提交。

> 1. 在提交工具窗口中，选择包含要添加到先前提交的更改的修改文件。`Alt` `0`
> 2. 选中“修改”复选框，使“提交”按钮更改为“修改提交”并单击它。

**3、修改任何先前的提交**﻿

如果您需要向任何早期提交添加更改而不是单独提交它们，则可以使用`fixup`或`squash`操作来完成此操作。这两个命令都将分阶段更改附加到所选提交，但处理提交消息的方式不同：

- `squash`将新的提交消息添加到原始提交中
- `fixup`丢弃新的提交消息，仅保留原始提交的消息

> 这两个命令都需要变[基](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)，因为它们更改了提交哈希值。

> 1. 在提交工具窗口中，选择包含要附加到早期提交的更改的修改文件。`Alt` `0`
> 2. 在 Git工具窗口 的 “日志”选项卡中，右键单击要使用本地更改进行修改的提交，然后从上下文菜单中选择“修复”或“压缩到” 。`Alt` `9`
> 3. 如果您选择压缩更改，请修改提交消息。
> 4. 单击Commit按钮上的箭头并选择Commit 和 Rebase。

**4、壁球提交**﻿

如果您需要合并与相同功能相关的任何两个提交，您可以将它们压缩为一个，以便更清晰的分支历史记录。

> 1. 在 Git工具窗口 的 “日志”选项卡中，选择要合并为一个的提交，然后从上下文菜单中选择“压缩提交” 。`Alt` `9`
> 2. 在打开的对话框中，编辑提交消息（默认情况下，它包含来自两次提交的消息），然后单击“确定”。
> 3. 将更改推送到远程分支。`Ctrl` `Shift` `K`

**5、删除提交**﻿

您可以放弃当前分支中推送的提交，而无需[创建恢复更改的附加提交](https://intellijidea.com.cn/help/idea/undo-changes.html#revert-commit)。

> - 在日志视图中选择要放弃的提交，然后从上下文菜单中选择“删除提交” 。

**6、通过执行交互式变基来编辑项目历史记录**﻿

通过 IntelliJ IDEA 中的 Git 集成，您可以通过执行交互式 rebase来编辑项目历史记录，使其线性且有意义。[这允许您在将更改从功能分支集成到另一个分支之前，通过更改单个提交、更改其顺序、将提交压缩为一个、跳过](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#feature-branches)[包含](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html)无关更改的提交等来清理提交历史记录。

> **编辑当前分支的历史记录**﻿
>
> IntelliJ IDEA 允许您在将更改应用到不同分支之前编辑当前分支中的提交历史记录。
>
> 1. 打开 Git工具窗口 并切换到“日志”选项卡。`Alt` `9`
>
> 2. 过滤日志，使其仅显示当前分支的提交：
     >
     >    ![按分支过滤日志](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_log_branch_filter.png)
>
> 3. 选择要编辑的一系列提交中最旧的提交，右键单击它并选择Interactively Rebase from Here。
     >
     >    将显示“交互式变基”对话框，其中包含当前分支中在选定提交之后进行的所有提交的列表：
     >
     >    ![交互式变基对话框](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_interactive_rebase_dialog.png)
     >
     >    如果“从此处交互式变基”选项被禁用，则可能是由于以下原因之一造成的：
     >
     >    - 所选提交有多个父项
>    - 所选提交不在当前分支中
>    - 选定的提交被推送到[受保护的分支](https://intellijidea.com.cn/help/idea/edit-project-history.html#protected-branch)
     >
     >    要确定原因，请将鼠标悬停在上下文菜单中的操作上，然后在状态栏中查找消息：
     >
     >    ![状态栏消息](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_interactive_rebase_disabled.png)
>
> 4. 您可以对分支历史记录执行以下更改：
     >
     >    - 更改应应用提交的顺序![向上箭头](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.arrowUp.svg)：使用和![向下箭头](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.arrowDown.svg)按钮在列表中上下移动提交。
>
>    - 选择一个提交：这是所有提交的默认状态。如果您需要撤消已对提交执行的操作，请单击“选择” ![应用程序操作回滚](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.rollback.svg)，以便按原样应用此提交。
>
>    - 编辑：单击“停止”进行编辑 ![暂停按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.pause.svg)，以便当您启动变基时，您可以在此提交处停止以便能够对其进行编辑。
       >
       >      > 当变基在提交时停止时，IntelliJ IDEA 窗口的右下角会弹出一条通知，让您继续或中止变基：
       >      >
       >      > ![变基状态通知](https://intellijidea.com.cn/help/img/idea/2023.2/continue_rebase_notification.png)
       >      >
       >      > 在继续变基之前，您可以使用上下文操作（例如Revert、Undo、Amend等）修改此提交。如果您不执行任何操作，则此提交将按原样应用。
       >      >
       >      > 如果您已关闭通知，请从主菜单中选择Git | 继续变基以恢复它。
>
>    - 重写提交消息：单击重写或双击提交并在打开的迷你编辑器中编辑文本。
>
>    - 将两个提交合并为一个：选择要合并到前一个提交中的提交，然后单击“Squash”或“Squash”按钮旁边的箭头，然后单击“Fixup”。
       >
       >      > 如果您单击Squash，默认情况下，来自两个提交的消息将被合并，因此，如果您不修改生成的提交消息，此操作将反映在分支历史记录中。
       >      >
       >      > 如果单击Fixup，则修复提交的提交消息将被丢弃，因此此更改将在分支历史记录中不可见。
       >      >
       >      > 在这两种情况下，您都可以在应用这些操作之一时打开的迷你编辑器中编辑提交消息。
>
>    - 忽略提交：单击“删除”，以便不应用所选提交的更改。
>
>    - 撤消所有更改：单击“重置”以放弃已应用于提交的所有操作。
     >
     >    因此，“变基提交”对话框会显示一个图表，说明您应用于分支中提交的所有操作，以便您可以在开始变基之前查看它们：
     >
     >    ![交互式变基图](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_interactive_rebase_graph.png)
>
> 5. 单击开始变基。

> **编辑分支历史并将其集成到另一个分支**﻿
>
> IntelliJ IDEA 允许您在另一个分支之上对一个分支[进行变基，并在应用更改之前编辑源分支历史记录。](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)
>
> 1. 从主菜单中选择 Git | 变基：
     >
     >    ![Git 变基对话框](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_dialog.png)
>
> 2. 单击修改选项并选择--interactive。
>
> 3. 从列表中，选择要将当前分支变基到的目标分支：
     >
     >    ![在 Git rebase 对话框中选择目标分支](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_choose_branch.png)
>
>
>
> 4. 如果您需要从特定提交开始对源分支进行变基，而不是对整个分支进行变基，请单击修改选项并选择--onto。在源分支字段中，输入要将当前分支应用到新基础的提交的哈希值：
     >
     >    ![使用 --onto 指定提交哈希](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_specify_commit.png)
     >
     >    > ### 
     >    >
     >    >
     >    >
     >    > 要复制提交哈希，请在Log中选择它，右键单击它并选择Copy Revision Number。
>
> 5. 如果您要变基的分支当前未签出，请单击“修改选项”，单击“选择另一个要变基的分支”，然后从显示的列表中选择一个分支：
     >
     >    ![选择您想要变基的分支](https://intellijidea.com.cn/help/img/idea/2023.2/git_rebase_choose_source_branch.png)
     >
     >    IntelliJ IDEA 将在开始变基操作之前检查此分支。
>
> 6. 如果要对分支中可访问的所有提交进行变基，请单击修改选项并选择--root（有关此选项的更多信息，请参阅[git-rebase](https://git-scm.com/docs/git-rebase)）。
>
> 7. 如果您需要保留空提交（即不会从其父级更改任何内容的提交），请单击修改选项并选择--keep-empty（有关此选项的更多信息，请参阅[git-rebase](https://git-scm.com/docs/git-rebase)）。
>
> 8. 单击变基。
     >
     >    将显示“交互式变基”对话框，其中包含当前分支中在选定提交之后进行的所有提交的列表。
     >
     >    ![交互式变基对话框](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_interactive_rebase_dialog.png)
>
> 9. 您可以对分支历史记录执行以下更改：
     >
     >    - 更改应应用提交的顺序![向上箭头](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.arrowUp.svg)：使用和![向下箭头](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.arrowDown.svg)按钮在列表中上下移动提交。
>
>    - 选择一个提交：这是所有提交的默认状态。如果您需要撤消已对提交执行的操作，请单击“选择” ![应用程序操作回滚](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.rollback.svg)，以便按原样应用此提交。
>
>    - 编辑：单击“停止”进行编辑 ![暂停按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.pause.svg)，以便当您启动变基时，您可以在此提交处停止以便能够对其进行编辑。
       >
       >      > 当变基在提交时停止时，IntelliJ IDEA 窗口的右下角会弹出一条通知，让您继续或中止变基：
       >      >
       >      > ![变基状态通知](https://intellijidea.com.cn/help/img/idea/2023.2/continue_rebase_notification.png)
       >      >
       >      > 在继续变基之前，您可以使用上下文操作（例如Revert、Undo、Amend等）修改此提交。如果您不执行任何操作，则此提交将按原样应用。
       >      >
       >      > 如果您已关闭通知，请从主菜单中选择Git | 继续变基以恢复它。
>
>    - 重写提交消息：单击重写或双击提交并在打开的迷你编辑器中编辑文本。
>
>    - 将两个提交合并为一个：选择要合并到前一个提交中的提交，然后单击“Squash”或“Squash”按钮旁边的箭头，然后单击“Fixup”。
       >
       >      > 如果您单击Squash，默认情况下，来自两个提交的消息将被合并，因此，如果您不修改生成的提交消息，此操作将反映在分支历史记录中。
       >      >
       >      > 如果单击Fixup，则修复提交的提交消息将被丢弃，因此此更改将在分支历史记录中不可见。
       >      >
       >      > 在这两种情况下，您都可以在应用这些操作之一时打开的迷你编辑器中编辑提交消息。
>
>    - 忽略提交：单击“删除”，以便不应用所选提交的更改。
>
>    - 撤消所有更改：单击“重置”以放弃已应用于提交的所有操作。
     >
     >    因此，“变基提交”对话框会显示一个图表，说明您应用于分支中提交的所有操作，以便您可以在开始变基之前查看它们：
     >
     >    ![交互式变基图](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_interactive_rebase_graph.png)
>
> 10. 单击开始变基。






















