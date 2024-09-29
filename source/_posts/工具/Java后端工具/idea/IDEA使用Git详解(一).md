---
title: IDEA 使用 Git 详解(一)
tags:
  - IDEA
categories:
  - 工具
description: IDEA 使用 Git 详解(一)
top_img: >-
  https://boosterminiclass.com/wp-content/uploads/2023/07/intellij_idea_git_2.png
cover: >-
  https://boosterminiclass.com/wp-content/uploads/2023/07/intellij_idea_git_2.png
date: '2024-09-25 14:45:02'
abbrlink: 7f7493d0
---

![ https://n.sinaimg.cn/sinakd10116/612/w2000h1012/20200629/34e0-ivrxcex3246619.jpg](https://n.sinaimg.cn/sinakd10116/612/w2000h1012/20200629/34e0-ivrxcex3246619.jpg)

# 版本控制

使用 `VSC` 操作弹出窗口或 `VSC|VSC 操作弹出窗口` 可快速调用任何 VSC 相关命令。`Alt ~`

弹出窗口中的操作列表取决于当前启用的 VSC 。

![vcs_operations_quick_list.png](https://intellijidea.com.cn/help/img/idea/2023.2/vcs_operations_quick_list.png)

> VSC 操作弹出命令列表是可配置的 - 你可以在 **外观和行为 | 上添加或删除它们** 。IDE 设置的 **菜单和工具栏页** 面。`Ctrl` `Alt` `S`

你还可以使用以下快捷键方式调用全局版本控制命令：

|                                                              |                          |
| ------------------------------------------------------------ | ------------------------ |
| VCS 操作弹出窗口...                                          | `Alt` `~`                |
| [犯罪...](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html) | `Ctrl` `K`               |
| [更新项目](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html) | `Ctrl` `T`               |
| [回滚](https://intellijidea.com.cn/help/idea/undo-changes.html) | `Ctrl` `Alt` `Z`         |
| [推...](https://intellijidea.com.cn/help/idea/using-git-integration.html) | `Ctrl` `Shift` `K`       |
| [下一个变化](https://intellijidea.com.cn/help/idea/viewing-changes-information.html) | `Ctrl` `Alt` `Shift` `↓` |
| [之前的变更](https://intellijidea.com.cn/help/idea/viewing-changes-information.html) | `Ctrl` `Alt` `Shift` `↑` |
| 显示版本控制窗口                                             | `Alt` `9`                |
| [显示提交窗口](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html) | `Alt` `0`                |



------

# 启用版本控制

**IntelliJ IDEA** 支持两个级别的版本控制集成：

- 在 IDE 级别，VSC 集成是通过一组默认启用的捆绑插件提供的。
- 在项目级别，通过将项目文件夹与一个或多个版本控制系统关联来启用 VSC 集成。



## 将项目根与版本控制系统关联

IntelliJ IDEA 允许快速启用项目与版本控制系统的集成，并将其与项目根相关联。

有关将单独的项目目录与不同版本控制系统关联的更多关系，请参阅 [将目录与版本控制系统关联](https://intellijidea.com.cn/help/idea/enabling-version-control.html#associate_directory_with_VCS) 。

<div style="border: 2px solid rgba(106,112,119,0.56)">
    <ol>
        <li>按打开 <b>VSC 操作弹出窗口</b> 并选择 <b>启用版本控制集成</b> 。<code>Alt</code> <code>~</code></li>
        <li>在打开的 <b>启用版本控制集成</b>对话框中，要选择要与 项目根关联的版本控制系统。</li>
        <li>启用 VSC 集成后，IntelliJ IDEA 会询问你是否要通过 VSC 共享项目设置文件。你可以选择 <b>始终添加</b> 以与使用 IntelliJ IDEA 的其他存储用户同步项目设置。
            <div>
            <img src="https://intellijidea.com.cn/help/img/idea/2023.2/sharing-project-notification.png" alt="自适应图片" style="width: 70%;height: auto;margin-left: 0">
            </div>
            请注意，这仅适用于 Git 和 Mercurial 。
        </li>
    </ol>
</div>


## 将目录与版本控制系统关联

IntelliJ IDEA 支持基于目录的版本控制模型，这意味着每个项目目录都可以与不同的版本控制系统关联。

<div style="border: 2px solid rgba(106,112,119,0.56)">
    <ol>
        <li>按打开 IDE 设置，然后选择 <b>版本控制 | 目录映射</b>。<code>Ctrl</code> <code>Alt</code> <code>S</code></li>
        <li><b>目录映射</b> 页面显示项目目录和与其关联的版本控制系统的列表（如果未添加目录，则该列表仅包含项目根目录）。</li>
        <li>单机右侧的 <b>添加</b> 按钮。<b>+</b></li>
        <li>在打开的 <b>添加 VSC 目录映射对话框中，选择 目录</b> 选项。输入要与版本控制系统关联的目录的路径，或者单机 <b>浏览</b> 按钮 📂 并在打开的对话框中选择目录。</li>
        <li>从 <b>VSC</b> 列表中，选择将用于控制此目录中的文件的版本控制系统。请注意，此列表仅包含当前启用相应插件的版本控制系统。</li>
        <li>单机 <b>确定</b> 保存映射并返回 <b>目录映射</b> 页面。</li>
    </ol>
</div>



管理未注册的目录

对于启用了 Git 或 Mercurial 集成的项目，IntelliJ IDEA 会扫描项目目录以检查是否存在不受 IDE 控制的 Git/Mercurial 存储库。如果检测到此类存储库，IntelliJ IDEA 会显示一条通知。

要添加未注册的根，请单击通知中的 **添加根链接** 。或者，打开版本控制设置页面，选择要添加的未注册根（他们标记为灰色），然后按照将目录与版本控制系统关联的过程进行操作。

如果你不想再次收到有关这些根的通知，请单机通知中的 **忽略链接** 。请注意，如果将新的未注册存储添加到项目中，IntelliJ IDEA 将通知你。

<div style="border: 2px solid rgba(106,112,119,0.56)">
    <div style="font-size: 1.5em; font-weight: bold;margin-left:10px;">更改 VCS 关联</div>
    <ol>
        <li>按打开 IDE 设置，然后选择 <b>版本控制 | 目录映射</b>。 <code>Ctrl</code> <code>Alt</code> <code>S</code></li>
        <li><b>目录映射</b> 页面显示项目目录和与其关联的版本控制系统的列表（如果未添加目录，则该列表仅包含项目根目录）。</li>
        <li>找到与要置于另一个版本控制系统下的目录相对应的行。</li>
        <li>单机 <b>VSC</b> 列。从出现的列表中，选择新的版本控制系统。
            如果你选择 <b>None</b> ，则将禁用所选目录的 VSC 集成。
        </li>
        <li>单机 <b>确定</b> 保存映射并返回 <b>目录映射</b> 页面。</li>
    </ol>
</div>


------



# 解决冲突

根据你的版本控制系统，在不同情况下可能会出现冲突。

当你在团队中工作时，你可能会遇到有人对你当前正在处理的文件提交更改的情况。如果这些更改**不重叠**（即，对不同的代码进行了更改），则会自动合并冲突。但是，如果相同的行受到影响，你的版本控制系统无法随机选择一侧而不是另一侧，并要求你解决冲突。

合并、变基或挑选分支时也可能会出现冲突。



## 非分布式版本控制系统

当你尝试变基服务器上具有较新版本的文件时， IntelliJ IDEA 会通知你，并在编辑器中显示一条弹出消息：

![冲突警告](https://intellijidea.com.cn/help/img/idea/2023.2/conflictMessageInEditor.png)

在这种情况下，你应该在更改文件之前更新本地版本或稍后合并更改。

如果你尝试提交具有较新存储库版本的文件，则会提交失败，并且右下角会显示一条错误，告诉你尝试提交的文件已过期。

> [失败的提交行为由版本控制 |中的](https://intellijidea.com.cn/help/idea/settings-version-control-confirmation.html)“在失败的提交列表上创建更改列表”控制。[设置](https://intellijidea.com.cn/help/idea/settings-preferences-dialog.html)对话框的[确认](https://intellijidea.com.cn/help/idea/settings-version-control-confirmation.html)页面。

如果将已进行本地更改的文件与其他人提交的较新存储库版本进行同步，则会发生冲突。冲突文件将获得“已合并冲突”状态。该文件保留在“更改”视图中的同一更改列表中 ，但其名称以红色突出显示。如果文件当前在编辑器中打开，选项卡标题上的文件名也会以红色突出显示。



------



## 分布式版本控制系统﻿

在分布式版本控制系统（例如 Git 和 Mercurial）下，当您在本地提交的文件对与最新上游版本相同的代码行进行更改时，以及当您尝试执行以下操作之一时，就会出现冲突：[pull](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#pull)、[merge](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)、[rebase](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)、[cherry-pick](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#cherry-pick)、[unstash](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#unstash)或[apply patch](https://intellijidea.com.cn/help/idea/using-patches.html)。

如果存在冲突，这些操作将失败，并且系统将提示您接受上游版本、首选您的版本或手动合并更改：

![IntelliJ IDEA：VCS 操作冲突对话框](https://intellijidea.com.cn/help/img/idea/2023.2/merge_conflicts_dialog.png)

当在版本控制级别检测到冲突时，会自动触发“冲突”对话框。

如果您在此对话框中单击“关闭”或从命令行调用导致合并冲突的 Git 操作，则“本地更改”视图中将出现“合并冲突”节点，并提供用于解决这些问题的链接：

![本地更改视图中的合并冲突节点](https://intellijidea.com.cn/help/img/idea/2023.2/git_merge_conflicts_node.png)

IntelliJ IDEA 提供了一个在本地解决冲突的工具。该工具由三个窗格组成：

- 左侧窗格显示只读本地副本
- 右窗格显示签入存储库的只读版本
- 中央窗格显示一个功能齐全的编辑器，其中显示合并和冲突解决的结果。最初，此窗格的内容与文件的基本修订版本相同，即派生两个冲突版本的修订版本。

![冲突解决工具中的颜色编码](https://intellijidea.com.cn/help/img/idea/2023.2/conflict_resolution_tool_legend.png)

**1、解决冲突**﻿

1. 单击“冲突”对话框中的“合并”、“本地更改”视图中的“解决”链接，或在编辑器中选择冲突文件并选择“VCS | ”。<您的VCS> | 从主菜单解决冲突。

2. 要自动合并所有不冲突的更改，请单击工具栏上的![应用不冲突的更改按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.applyNotConflicts.svg)(应用所有不冲突的更改)。您还可以使用![从左侧应用不冲突的更改按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.applyNotConflictsLeft.svg)（从左侧应用非冲突更改）和![从右侧按钮应用不冲突的更改](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.applyNotConflictsRight.svg)（从右侧应用非冲突更改）分别合并对话框左/右部分的非冲突更改。

3. 要解决冲突，您需要选择对左侧（本地）和右侧（存储库）版本应用哪个操作（接受![接受按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.arrow.svg)或忽略），并在中央窗格中检查生成的代码：![忽略按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.remove.svg)

   ![解决冲突](https://intellijidea.com.cn/help/img/idea/2023.2/resolveConflict.png)

   您还可以右键单击中央窗格中突出显示的冲突，然后使用上下文菜单中的命令。使用左侧解决和使用右侧解决命令分别提供了从一侧接受更改并从另一侧忽略更改的快捷方式：

   ![冲突更改的上下文菜单](https://intellijidea.com.cn/help/img/idea/2023.2/resolve_using_left_right.png)

   对于简单冲突（例如，如果同一行的开头和结尾已在不同的文件修订版中修改），可以使用“解决简单冲突” ![解决简单冲突按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.diff.magicResolve.svg)按钮，该按钮允许一键合并更改。

   ![解决简单冲突按钮](https://intellijidea.com.cn/help/img/idea/2023.2/simple_conflict_resolve.png)

   此类冲突无法通过“应用所有非冲突更改”操作来解决，因为您必须确保它们得到正确解决。

   > ### 
   >
   > 
   >
   > 请注意，中央窗格是一个功能齐全的编辑器，因此您可以直接在此对话框中更改结果代码。

4. 比较不同版本以解决冲突也可能很有用。使用![比较内容按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)工具栏按钮调用选项列表。请注意，Base是指本地版本和存储库版本源自的文件版本（最初显示在中间窗格中），而Middle是指结果版本。

5. 在中央窗格中查看合并结果，然后单击“应用”。

**2、生产力技巧**﻿

自动应用不冲突的更改

您可以将 IntelliJ IDEA 配置为始终自动应用不冲突的更改，而不是从“合并”对话框中告诉它这样做。为此，请选择“工具”| “自动应用不冲突的更改”选项。IDE 设置的 Diff Merge页面。`Ctrl` `Alt` `S`

在中央窗格中管理更改

您可以使用将鼠标悬停在装订线中的更改标记上然后单击它时出现的工具栏来管理中央窗格中的更改。工具栏与一个框架一起显示，该框架显示修改行的先前内容：

![更改工具栏](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts_change_toolbar.png)



例如，当存在多个不冲突的更改时，您只需跳过其中一两个更改，则可以更轻松地使用“应用所有不冲突的更改”操作同时应用所有更改，然后使用“还原”撤消不需要的更改。从此工具栏执行操作。



------

# VCS 与问题跟踪器集成

借助 IntelliJ IDEA，您可以将提交消息与错误跟踪器或问题数据库连接起来，并从 VCS 日志中的提交导航到与这些提交相关的问题。

**1、启用从提交消息到问题的导航**﻿

1. 按打开 IDE 设置，然后选择版本控制 | 问题导航。`Ctrl` `Alt` `S`

2. 通过将提交消息中的问题模式与引用问题的 URL 地址进行映射来配置问题导航模式列表。

   - 如果您使用[JIRA](http://www.atlassian.com/software/jira/overview)或[YouTrack](http://www.jetbrains.com/youtrack/)，请单击工具栏上的“添加 JIRA 模式” ![应用程序工具栏装饰器添加 jira](https://intellijidea.com.cn/help/img/idea/2023.2/app.toolbarDecorator.addJira.svg)或“添加 YouTrack 模式” ，然后键入安装错误跟踪系统的 URL。 ![应用程序工具栏装饰器添加您的轨道](https://intellijidea.com.cn/help/img/idea/2023.2/app.toolbarDecorator.addYouTrack.svg)

     IntelliJ IDEA 将自动添加定义导航模式的正则表达式。

   - 对于其他问题跟踪系统，单击添加按钮![应用程序常规添加](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.add.svg)创建新条目或选择现有条目并单击编辑按钮。在打开的“添加问题导航链接”对话框中，指定以下正则表达式：

     - 提交消息中[问题 ID 的](https://intellijidea.com.cn/help/idea/handling-issues.html#example_issue_id_pattern)模式
     - 定义用于访问相应引用问题的 URL 的[替换](https://intellijidea.com.cn/help/idea/handling-issues.html#example_issue_link_pattern)表达式

**2、例子**﻿

| 问题ID         | 定义提交消息中问题引用格式的[正则表达式](https://intellijidea.com.cn/help/idea/regular-expressions.html)。`[A-Z]+\-\d+`此正则表达式匹配由 n 破折号字符分隔的两个子字符串组成的所有字符串：子字符串 1：无限数量的大写字母字符。子字符串 2：无限数量的数字字符。 |
| -------------- | ------------------------------------------------------------ |
| 问题链接       | 问题跟踪系统的 URL 地址和标识其中问题的正则表达式的组合。`http://<mytracker>/issue/$0`这里`$0`表示对整个比赛的反向引用。这意味着，一旦 IntelliJ IDEA 检测到提交消息中的匹配项，它就会按原样添加到跟踪器的 URL 地址中。 |
| 匹配问题 ID    | IntelliJ IDEA 在感兴趣的提交消息中检测到以下对问题的引用：`MYPROJECT-110` |
| 组成的问题链接 | 根据上述问题导航模式，检测到的匹配引用按原样添加到跟踪器的 URL 中，因此指向引用问题的链接组成如下：`http://mytracker/issue/MYPROJECT-110` |



------



# 管理变更列表

更改列表是一组尚未提交到 VCS 存储库的本地更改。

使用变更列表，你可以对与不同任务相关的变更进行分组，并独立提交这些变更集。有关更多信息，请参阅[在本地提交更改](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#commit)。

> 如果您使用 Git，变更列表只是[同时处理多个功能的](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#changelists_intro)方法之一。
>

更改列表显示在**更改**视图中。最初，有一个名为 **Changes** 的默认更改列表。所有新更改都会自动放入 **更改** 更改列表中。还有一个 **未版本控制的文件更改列表**，用于对**尚未**添加到 VCS 中的新创建的文件进行分组。

![提交工具窗口中的更改列表](https://intellijidea.com.cn/help/img/idea/2023.2/changelists_in_commit_tw.png)

你可以根据需要创建任意数量的更改列表，并随时使其中任何一个更改列表处于活动状态。你可以将任何未提交的更改移至任何更改列表。

**1、创建新的变更列表**﻿

1. 在“本地更改”视图中，单击![更改列表图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.changelist.svg)工具栏上的 并选择“新建更改列表”。
2. 在“新建更改列表”对话框中，指定新更改列表的名称，并添加说明（可选）。

**2、设置活动变更列表**﻿

- 在“本地更改”视图中，选择一个非活动更改列表，然后按或右键单击它，然后从上下文菜单中选择“设置活动更改列表” 。所有新的更改都会自动放入此更改列表中。`Ctrl` `Space`

**3、在更改列表之间移动更改**﻿

1. 在“本地更改”视图中，选择要移动到另一个更改列表的更改。
2. 右键单击所选内容或单击![更改列表图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.changelist.svg)工具栏上的 并选择“移动到另一个更改列表” 。`Alt` `Shift` `M`
3. 在打开的对话框中，选择现有变更列表或输入新变更列表的名称。
4. 您可以选择使目标更改列表处于活动状态并跟踪其上下文（IntelliJ IDEA 将保存与此更改列表关联的上下文，并在该更改列表变为活动状态时恢复它）。

> 您还可以在更改列表之间拖动文件。

> 有关将一个文件中的更改放入 Git 中的不同更改列表的更多信息，请参阅将[更改放入不同的更改列表](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#put_changes_into_different_changelists)。

**4、删除变更列表**﻿

- 右键单击更改列表，然后从上下文菜单中选择“删除更改列表” 。



------

# 搁置和取消搁置更改

取消搁置更改：`Ctrl` `Shift` `U`

搁置是暂时存储您尚未提交的待处理更改。例如，如果您需要切换到另一个任务，并且希望将更改放在一边以供稍后处理，则这非常有用。

使用 IntelliJ IDEA，您可以搁置单独的文件和整个变更列表。

> 您无法搁置未版本化的文件，即尚未[添加到版本控制的](https://intellijidea.com.cn/help/idea/adding-files-to-version-control.html#add-files-to-vcs)文件。

搁置后，可以根据需要多次应用更改。



## 搁置变更﻿

1. 在 “提交”工具窗口中，右键单击要搁置的文件或更改列表，然后从上下文菜单中选择“搁置更改” 。`Alt` `0`

   ![搁置变化](https://intellijidea.com.cn/help/img/idea/2023.2/shelve-changes.png)

2. 在“搁置更改”对话框中，查看已修改文件的列表。

3. 在“提交消息”字段中，输入要创建的架子的名称，然后单击“架子更改”按钮。

您还可以静默搁置更改，而不显示“搁置更改”对话框。为此，请选择要搁置的文件或更改列表，然后单击工具栏上的“静默搁置”图标或按。包含要搁置的更改的更改列表的名称将用作搁置名称。![默默搁置](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.shelveSilent.svg)`Ctrl` `Shift` `H`

为了避免出现多个同名的架子（例如Default），您可以将文件或更改列表从“提交到 <branch>”选项卡拖到“提交”工具窗口的“架子”选项卡，稍等片刻直到它被激活，释放鼠标按钮后编辑新的架子名称。

> 如果您需要将更改复制到架子而不重置本地更改，请按并查找“保存到架子”操作。`Ctrl` `Shift` `A`



## 取消搁置变更﻿

取消搁置是将推迟的更改从搁架移动到待处理的更改列表。未搁置的更改可以从视图中过滤掉或从搁置中删除。

1. 在[“搁置”](https://intellijidea.com.cn/help/idea/shelf-tab.html)选项卡中，选择更改列表或要取消搁置的文件。

2. 按或从所选内容的上下文菜单中选择“取消搁置” 。`Ctrl` `Shift` `U`

   ![取消搁置变更](https://intellijidea.com.cn/help/img/idea/2023.2/py_unshelve_changes.png)

3. 在“取消搁置更改”对话框中，在“名称”字段中指定要将未搁置的更改恢复到的更改列表。您可以从列表中选择现有变更列表或输入要创建的新变更列表的名称。您可以在注释字段中输入新变更列表的描述（可选）。

   如果您想让新的更改列表处于活动状态，请选择“设置活动”。否则，当前活动变更列表保持活动状态。

4. 如果您希望 IntelliJ IDEA 在停用时保存与新变更列表关联的任务的上下文，并在变更列表变为活动状态时恢复上下文，请选择“跟踪上下文”选项（有关详细信息，请参阅[任务和上下文）。](https://intellijidea.com.cn/help/idea/managing-tasks-and-context.html)

5. 如果要删除要取消搁置的更改，请选择“从搁置中删除已成功应用的文件”选项。未搁置的文件将从该搁置中删除，添加到另一个更改列表中，并标记为已应用。![删除图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.gc.svg)只有通过单击工具栏上的 或从上下文菜单中选择清理已取消搁置来明确删除它们，它们才会被完全删除。

   > 如果您意外删除了未搁置的文件，您可以从“最近删除”节点查看和恢复它们。

6. 单击“确定”。如果修补版本与当前版本发生冲突，请按照[解决冲突](https://intellijidea.com.cn/help/idea/resolving-conflicts.html)中的说明进行解决。

您还可以静默取消搁置更改，而不显示“取消搁置更改”对话框。为此，请选择要取消搁置的文件或更改列表，然后单击工具栏上的“静默取消搁置”图标或按。未搁置的文件将移至活动的挂起更改列表。![默默取消搁置图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.unshelveSilent.svg)`Ctrl` `Alt` `U`

您还可以将文件或更改列表从“搁置”选项卡拖到“提交到 <branch>”选项卡以静默取消搁置。如果按住键拖动它，它将被复制到“提交到分支”选项卡，但也会保留在架子中。`Ctrl`

## 放弃搁置的更改﻿

1. 在“书架”视图中，选择包含您不想再保留的更改的更改列表。
2. 右键单击更改列表，然后从上下文菜单中选择“删除”或按。`Delete`

## 恢复未搁置的更改﻿

IntelliJ IDEA 允许您在必要时重新应用未搁置的更改。所有未搁置的更改都可以重复使用，直到通过单击![删除未搁置的更改](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.gc.svg)工具栏上的图标或从上下文菜单中选择“清理已未搁置”来明确删除它们为止。

1. 确保已启用显示已取消搁置的工具栏选项。 ![显示已下架按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.patch_applied.svg)
2. 选择要恢复的文件或架子。
3. 从所选内容的上下文菜单中，选择“恢复”。

## 应用外部补丁﻿

您可以导入在 IntelliJ IDEA 内部或外部创建的补丁，并将它们作为搁置的更改应用。

1. 在 Shelf 视图中，从上下文菜单中选择Import Patches 。
2. 在打开的对话框中，选择要应用的补丁文件。选定的补丁将在“Shelf”选项卡中显示为“shelf”。
3. 选择新添加的带有补丁的架子，然后从所选内容的上下文菜单中选择“取消搁置更改” 。

## 自动搁置基础修订﻿

将 IntelliJ IDEA 配置为始终搁置受 Git 版本控制的文件的基本修订版本可能很有用。

1. 按打开 IDE 设置，然后选择**版本控制 | 架子**。`Ctrl` `Alt` `S`

2. 选择“在分布式版本控制系统下搁置文件的基本修订版本”选项。

   如果启用此选项，文件的基本修订版本将保存到架子上，如果应用架子导致冲突，则该架子将在[三向合并](https://en.wikipedia.org/wiki/Merge_(version_control)#Three-way_merge)期间使用。如果禁用，IntelliJ IDEA 将在项目历史记录中查找基础修订版，这可能需要一段时间；此外，冲突架所基于的修订可能会丢失（例如，如果历史记录因变基操作而更改）。

## 更改默认架子位置﻿

默认情况下，shelf 目录位于您的项目目录下。但是，您可能想要更改默认的架子位置。例如，如果您想避免在清理工作副本时意外删除架子，或者希望将它们存储在单独的存储库中，以便在团队成员之间共享架子，这可能很有用。

1. 按打开 IDE 设置，然后选择**版本控制 | 架子**。`Ctrl` `Alt` `S`
2. 单击更改书架位置并在打开的对话框中指定新位置。
3. 如有必要，选择将架子移动到新位置以将现有架子移动到新目录。



------

# 使用补丁

您可以将其放入 **.patch** 文件中，而不是提交本地更改，您可以稍后将其应用到源、通过电子邮件发送等。使用补丁是一种共享更改的便捷机制，无需在 VCS 存储库中检查它们。

## 从未提交的更改创建补丁﻿

1. 在“本地更改”视图中，选择要包含在补丁中的文件或更改列表，然后从上下文菜单中选择“从本地更改创建补丁” 。

   您还可以选择提交更改：单击“提交”按钮旁边的箭头，然后选择“创建补丁”。

2. 在打开的对话框中，确保选择要包含在补丁中的所有更改，输入提交注释（可选），然后单击“创建补丁”。

3. 在“修补程序文件设置”对话框中，根据需要修改默认修补程序文件位置，然后单击“确定”。

如果您不需要将补丁保存到文件中（例如，您想通过电子邮件发送补丁），请在“更改”视图中右键单击必要的文件，然后从上下文菜单中选择“复制为 补丁到剪贴板”。

## 从整个提交创建补丁﻿

1. 在 版本控制工具窗口 的 “日志”选项卡中，找到包含要包含在补丁中的更改的提交，然后从上下文菜单中选择“创建补丁” 。`Alt` `9`
2. 在“修补程序文件设置”对话框中，根据需要修改默认修补程序文件位置，然后单击“确定”。

## 从文件创建补丁﻿

1. 在任何视图（项目工具窗口、编辑器、 更改视图等）中选择必要的文件。
2. 选择Git | 从VCS主菜单或选择的上下文菜单显示历史记录。“历史记录”选项卡已添加到 Git工具窗口，显示所选文件的历史记录，并允许您查看和比较其修订版本。
3. 右键单击修订版本并从上下文菜单中选择“创建补丁”或单击工具栏上的“创建补丁”图标。![应用补丁图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.patch.svg)

## 应用补丁﻿

1. 选择VCS | 补丁| 从主菜单应用补丁。

2. 在打开的“应用补丁”对话框中，指定要应用的.patch文件的路径。

   > 您可以将文件或电子邮件附件拖到编辑器中的任何位置。

3. 如有必要，单击![文件夹图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.folders.svg)并选择“映射基本目录”以指定相对于补丁文件中的文件名进行解释的目录。您可以将基本目录映射到单个文件、目录或选择。

4. 如果在创建补丁后编辑源代码，可能会出现冲突。要检查您的补丁是否可以在不发生冲突的情况下应用，请单击“显示差异” 。如果存在冲突，相应的行将以红色突出显示。![显示差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg) `Ctrl` `D`

5. 如果您想要将更改应用于存储在补丁中指定位置以外的位置的文件，您可以通过单击 并![文件夹图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.folders.svg)选择“删除所有前导目录”来去除前导目录。

6. 选择要应用补丁的变更列表，或在“名称”字段中指定新变更列表的名称，然后为此变更列表输入注释（可选）。

7. 如果您想让此更改列表处于活动状态，请选择“设置为活动”选项。

8. 如果您希望 IntelliJ IDEA 在停用时保存与新变更列表关联的任务的上下文，并在变更列表变为活动状态时恢复上下文，请选择“跟踪上下文”选项（有关详细信息，请参阅[任务和上下文）。](https://intellijidea.com.cn/help/idea/managing-tasks-and-context.html)

9. 如果您想在应用补丁之前将其移动到临时存储（搁架），请单击导入到搁架（有关详细信息，请参阅[搁置和取消搁置更改](https://intellijidea.com.cn/help/idea/shelving-and-unshelving-changes.html)）。否则，请单击“确定”。

您还可以通过选择VCS |复制补丁文件的内容并应用它。从主菜单应用剪贴板补丁。例如，当您通过电子邮件收到补丁但不想保存它时，这会很方便。对于[Git 格式的](https://git-scm.com/docs/git-format-patch)补丁，IntelliJ IDEA 会提取提交消息和作者，并自动填充 Commit工具窗口中的相应字段。`Alt` `0`



------

# 审查变更

本主题说明如何跟踪您和您的团队成员对源代码所做的更改。

## 回顾项目历史﻿

IntelliJ IDEA 允许您查看对与指定过滤器匹配的项目源所做的所有更改。

对于分布式版本控制系统，例如 Git 和 Mercurial，您可以在 版本控制工具窗口 的日志选项卡 中查看项目历史记录（请参阅[调查 Git 存储库中的更改](https://intellijidea.com.cn/help/idea/investigate-changes.html)）。`Alt` `9`

对于集中式版本控制系统，例如 Subversion、Perforce 和 ClearCase，项目历史记录可在版本控制工具窗口 的 [存储库选项卡](https://intellijidea.com.cn/help/idea/version-control-tool-window-repository-and-incoming-tabs.html)中找到。`Alt` `9`

## 在编辑器中跟踪文件的更改﻿

当您修改受版本控制的文件时，所有更改都会在编辑器中突出显示，并带有更改标记，这些标记出现在修改行旁边的装订线中，并显示自上次与存储库同步以来引入的更改类型。当您将修改后的文件提交到存储库时，更改标记就会消失。

您对文本所做的更改是用颜色编码的：

- ![新添加行的标记](https://intellijidea.com.cn/help/img/idea/2023.2/lineAddedMarker.png)已添加行。
- ![修改行的标记](https://intellijidea.com.cn/help/img/idea/2023.2/lineChangededMarker.png)线路改变了。
- ![已删除行的标记](https://intellijidea.com.cn/help/img/idea/2023.2/lineDeletedMarker.png)行已删除。

> 您可以在编辑器 |上自定义线路状态的默认颜色。配色方案| IDE 设置的 VCS页面。`Ctrl` `Alt` `S`
>
> 要禁用装订线中的 VCS 标记，请取消选择“版本控制”| “装订线”中的“突出显示装订线中已修改的行”选项。IDE 设置的 确认页面。`Ctrl` `Alt` `S`

您可以使用专用工具栏管理更改。要调用它，请将鼠标悬停在更改标记上，然后单击它。工具栏与一个框架一起显示，该框架显示修改行的先前内容：

![更改标记工具栏](https://intellijidea.com.cn/help/img/idea/2023.2/changeMarkerToolbar.png)

工具栏中的操作可让您导航到下一个或上一个更改、回滚更改、查看当前版本与存储库版本之间的差异、将修改行的先前版本复制到剪贴板，或者打开突出显示代码中的差异。

如果要关闭突出显示更改，请取消选中版本控制 |上的突出显示装订线中修改的行选项。IDE 设置的 确认页面。`Ctrl` `Alt` `S`

## 将本地更改与存储库版本进行比较﻿

除了在编辑器中[浏览](https://intellijidea.com.cn/help/idea/viewing-changes-information.html#local_changes)文件中的本地更改之外，您还可以将这些更改与文件的基本修订版进行比较。

要预览差异，请在“提交”工具窗口中选择修改后的文件，然后单击![应用程序操作差异](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)工具栏上的 。

左侧窗格显示基本修订版中受影响的代码，右侧页面显示您在本地进行更改后受影响的代码。

![编辑器中的差异预览](https://intellijidea.com.cn/help/img/idea/2023.2/ij_diff_in_editor.jpg)

使用工具栏按钮和控件在更改之间导航并配置更改详细信息窗格或差异查看器的外观：

| 物品                                                         | 工具提示和快捷方式                                           | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![上一个差异按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.up.svg)/![下一个差异按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.down.svg) | 上一个差异/下一个差异 `Shift` `F7` `F7`                      | 跳转到下一个或上一个差异。当达到最后一个或第一个差异时，IntelliJ IDEA 建议单击箭头按钮或再次按/并比较本地修改的其他文件。此行为取决于[“差异查看器”设置中的](https://intellijidea.com.cn/help/idea/settings-tools-diff-and-merge.html)[“到达最后一次更改后转到下一个文件”](https://intellijidea.com.cn/help/idea/settings-tools-diff-and-merge.html#last_diff)选项。`F7` `Shift` `F7` |
| ![跳转到源按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.edit.svg) | 跳转至源代码 `F4`                                            | 在编辑器中打开选定的文件。插入符号的位置与差异查看器中的位置相同。 |
| ![比较上一个文件图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.left.svg)![比较下一个文件图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.right.svg) | 比较上一个/下一个文件`Alt` `←`  `Alt` `→`                    | 将上一个或下一个文件的本地副本与其来自服务器的更新进行比较。仅当本地修改了多个文件时，这些控件才可用。 |
| ![转到已更改的文件图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.listFiles.svg) | 转到已更改的文件 `Ctrl` `0N`                                 | 显示当前更改集中所有已更改的文件并导航到它们。仅当您查看对多个文件的更改时，此操作才可用。 |
| 观众                                                         | 选择查看器模式：并排或统一。并排模式有两个面板，统一模式有一个面板。您可以在两个查看器中编辑代码并执行Accept、Append、Revert操作。您只能更改并排查看器的右侧部分或统一查看器的下一行中的文本。您只能编辑文件的本地版本。您无法编辑具有只读状态的文件。 |                                                              |
| 空白                                                         | 定义差异查看器应如何处理空格。不要忽视：空白很重要，并且所有差异都会突出显示。默认情况下选择此选项。修剪空白：修剪出现在行尾和行首的空白 ( `("\t", " ")`)。如果两行仅尾随空格不同，则这些行被视为相等。如果两行不同，则在[按字](https://intellijidea.com.cn/help/idea/viewing-changes-information.html#highlight)模式下不会突出显示尾随空格。忽略空格：空格并不重要，无论它们在源代码中的位置如何。忽略空格和空行：忽略空格和空行。以下实体将被忽略：所有空格（如“忽略空格”选项中所示）所有添加或删除的行仅由空格组成所有由分割或连接行组成的更改，而不更改非空白部分。例如，在此模式下不会突出显示`a b c`和之间的差异。`a \n b c`忽略导入和格式设置：导入语句中的更改和空格将被忽略（但会考虑字符串文字中的空格）。 |                                                              |
| 突出显示模式                                                 | 选择突出显示差异粒度的方式。可用的选项有：高亮单词：修改后的单词高亮显示高亮行：修改的行高亮显示突出显示拆分更改：如果选择此选项，则大更改将拆分为较小的更改。例如，`A \n B`和`A X \n B X`被视为两项更改而不是一项。高亮字符：修改后的符号高亮显示不突出显示：如果选择此选项，则根本不突出显示差异。当您处理经过重大修改的文件时，请使用“不突出显示”选项。在这种情况下，突出显示可能会在审核过程中带来额外的困难。 |                                                              |
| ![折叠未更改的片段图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.collapseAll.svg) | 折叠未更改的片段                                             | 折叠两个文件中所有未更改的片段。不可折叠的未更改行的数量可在“差异和合并”设置页面上进行配置。要打开“差异和合并”页面，请按打开设置，然后导航到“工具”\|“ 差异与合并。CtrlAlt0S |
| ![同步按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.actions.synchronizeScrolling.svg) | 同步滚动                                                     | 单击此按钮可同时滚动两个差异窗格。如果释放此按钮，每个窗格都可以独立滚动。 |
| ![设置按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.settings.svg) | 设置                                                         | 打开可用设置的列表。也可以从差异查看器装订线的上下文菜单中使用这些命令。 |
| ![外部工具图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.externalTools.svg) | 在外部工具中显示差异                                         | 调用外部差异[工具](https://intellijidea.com.cn/help/idea/settings-tools-external-diff-tools.html)设置页面上指定的外部差异查看器。仅当在外部比较工具设置页面上启用使用外部[比较](https://intellijidea.com.cn/help/idea/settings-tools-external-diff-tools.html)工具选项时，此按钮才在工具栏上可用。 |
| ![帮助图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.help.svg) | 帮助 `F1`                                                    | 打开浏览器并显示相应的帮助页面。                             |
|                                                              | 使用 GitBlame 进行注释                                       | 此选项只能从装订线的上下文菜单中使用。使用此选项可以探索谁对文件的存储库版本进行了哪些更改以及何时进行。通过注释视图，您可以查看每行代码的详细信息，例如该行源自的版本、提交该行的用户的 ID 以及提交日期。有关注释的更多信息，请参阅[VCS 注释](https://intellijidea.com.cn/help/idea/viewing-changes-information.html#annotations)。 |

最有用的快捷键如下：

| 捷径                            | 描述                                                        |
| ------------------------------- | ----------------------------------------------------------- |
| `Ctrl` `Shift` `D`              | 使用此键盘快捷键可显示最常用的 diff 命令的弹出菜单。        |
| `Ctrl` `Shift` `Tab`            | 使用此键盘快捷键可在左窗格和右窗格之间切换。                |
| `Ctrl` `Z` / `Ctrl` `Shift` `Z` | 使用此键盘快捷键可撤消/重做合并操作。冲突将与文本保持同步。 |

## 查看文件或选择的更改历史记录﻿

IntelliJ IDEA 允许您查看对文件甚至源代码片段所做的更改。“显示历史记录”和“显示选择历史记录”命令可从VCS主菜单和文件的上下文菜单中使用。

文件的更改历史记录显示在版本控制工具窗口 的 专用[历史记录选项卡](https://intellijidea.com.cn/help/idea/version-control-tool-window-history-tab.html)中。`Alt` `9`

[所选代码的更改历史记录以差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)的形式显示在单独的窗口中。

**1、查看文件历史记录**﻿

- 在编辑器中打开文件或在项目工具窗口中选择它并选择<VCS> | 从上下文菜单中显示历史记录。

所选文件的 [“历史记录”](https://intellijidea.com.cn/help/idea/version-control-tool-window-history-tab.html)选项卡出现在版本控制工具窗口 中，文件名显示在选项卡的标题栏上。`Alt` `9`

您可以使用[工具栏](https://intellijidea.com.cn/help/idea/version-control-tool-window-history-tab.html)按钮将所选版本与本地版本进行比较、比较所选版本中的类、从 VCS 中检出所选版本、注释所选版本等：

| 物品                                                         | 工具提示和快捷方式                    | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------- | ------------------------------------------------------------ |
| ![刷新按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.refresh.svg) | 刷新                                  | 单击此按钮可刷新当前信息。                                   |
| ![显示差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg) | 显示差异 `Ctrl` `D`                   | 单击此按钮可将文件的选定版本与[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)中的先前版本进行比较。 |
| ![显示所有受影响的文件按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.listChanges.svg) | 显示所有受影响的文件`Alt` `Shift` `A` | 单击此按钮可打开“修订版中受影响的路径”对话框，您可以在其中查看在选定修订版中修改的所有文件。 |
| ![显示所有分支按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.branch.svg) | 显示所有分行                          | 单击此按钮可显示当前分支以外的分支的更改。                   |
| ![眼睛图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.show.svg) | 演示设置                              | 单击以选择您想要在“历史记录”视图中查看的信息量。如果您希望 IntelliJ IDEA 显示提交时间戳而不是创作更改的时间，您还可以选择“显示提交时间戳”选项。 |
| ![配置布局图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.debugger.restoreLayout.svg) | 配置布局                              | 单击以选择您要查看的信息类型：显示详细信息以显示所选修订的提交消息。显示差异预览以打开所选版本的差异预览。 |
| ![在 GitHub 上打开按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.vendors.github.svg) | 在 GitHub 中打开                      | [单击此按钮可打开与GitHub](https://github.com/)上所选提交对应的页面。 |

**2、查看选择的历史记录**﻿

1. 在编辑器中，选择必要的源代码片段或将插入符号放在相应的行上。
2. 选择<VCS> | 从主VCS菜单或选择的上下文菜单显示选择的历史记录。

所选片段的历史记录将在单独的窗口中打开。如果未选择任何内容，将显示当前行的历史记录。



## 检查文件状态﻿

IntelliJ IDEA 允许您检查项目文件相对于存储库的状态。文件状态显示自上次与存储库同步以来已对文件执行了哪些操作。

您可以通过用于突出显示文件名的颜色在任何界面元素（例如编辑器或工具窗口）中检查文件的状态。

[您可以在“颜色和字体”](https://intellijidea.com.cn/help/idea/settings-colors-and-fonts.html)设置页面中自定义文件状态的默认颜色。

您可以在版本控制 |配置 VCS 文件状态颜色 IDE 设置的 文件状态颜色页面。`Ctrl` `Alt` `S`

> 要同时突出显示包含已修改内容的文件夹和包，请在版本控制 |项目树中选择突出显示包含已修改文件的目录。IDE 设置的 确认页面。CtrlAlt0S

下表列出了默认文件状态颜色及其在某些[配色方案](https://intellijidea.com.cn/help/idea/configuring-colors-and-fonts.html)中的含义。



**浅色主题**

| 颜色                                                         | 文件状态               | 描述                                                         |
| ------------------------------------------------------------ | ---------------------- | ------------------------------------------------------------ |
| ![颜色样本： 深绿色](https://intellijidea.com.cn/help/img/idea/2023.2/added-light.png) #0A7700 | 添加                   | [活动变更列表](https://intellijidea.com.cn/help/idea/managing-changelists.html)中的文件计划添加到存储库中。 |
| ![颜色样本： 绿色](https://intellijidea.com.cn/help/img/idea/2023.2/added-inactive-changelist-light.png) #0EAA00 | 添加到非活动变更列表中 | 非活动更改列表中的文件计划添加到存储库中。如果在“设置”\| “突出显示非活动更改列表中的文件”选项已启用，则此文件状态可用。版本控制 \| 变更列表。 |
| ![颜色样本： 红色](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-light.png) #FF0000 | 变更列表冲突           | 非活动变更列表中的文件已在活动变更列表中被修改。在这种情况下，将打开一个新对话框，提示您解决[更改列表冲突](https://intellijidea.com.cn/help/idea/resolving-conflicts.html)。如果在“设置”\|“设置”中启用了所有选项，则此文件状态可用。版本控制 \| 变更列表。 |
| ![颜色样本： 深绿色](https://intellijidea.com.cn/help/img/idea/2023.2/added-light.png) #0A7700 | 已复制                 | 如果一个文件是另一个文件的副本，则会跟踪其元数据，并将此类文件标记为已复制。 |
| ![颜色样本：灰色](https://intellijidea.com.cn/help/img/idea/2023.2/deleted-light.png) #616161 | 已删除                 | 该文件计划从存储库中删除。                                   |
| ![颜色样本：暗紫色](https://intellijidea.com.cn/help/img/idea/2023.2/deleted-from-filesystem-light.png) #773895 | 从文件系统中删除       | 该文件已在本地删除，但尚未计划删除，并且仍然存在于存储库中。 |
| ![颜色样本：浅灰蓝色](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-light.png) #8AA4C8 | 改变了后代             | 如果文件被修改，IDE 将递归突出显示包含该文件的所有目录。如果在“设置”\| “项目树”中启用“突出显示项目树中包含已修改文件的目录”选项，则此状态可用。版本控制 \| 确认。 |
| ![颜色样本：亮蓝色](https://intellijidea.com.cn/help/img/idea/2023.2/changed-children-light.png) #3264B4 | 立即改变孩子           | 如果文件被修改，IDE 将突出显示其父目录。如果在“设置”\| “项目树”中启用“突出显示项目树中包含已修改文件的目录”选项，则此状态可用。版本控制 \| 确认。 |
| ![颜色样本： 浅棕色](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-light.png) #B28C00 | 被劫持                 | [Perforce、ClearCase、VSS] 文件被[修改但未签出。](https://intellijidea.com.cn/help/idea/handling-modified-without-checkout-files.html) |
| ![色样：深橄榄色](https://intellijidea.com.cn/help/img/idea/2023.2/ignored-light.png) #727238 | 被忽略                 | VCS 故意取消跟踪文件。                                       |
| ![颜色样本：紫色](https://intellijidea.com.cn/help/img/idea/2023.2/merged-light.png) 第7503章 DC | 合并                   | 作为更新的结果，该文件由您的 VCS 合并。                      |
| ![颜色样本： 红色](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-light.png) #FF0000 | 与冲突合并             | 在上次更新期间，该文件已合并并存在冲突。                     |
| ![颜色样本： 红色](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-light.png) #FF0000 | 合并财产冲突           | 在上次更新期间，IDE 检测到本地文件的属性与其服务器版本之间存在差异。 |
| ![颜色样本： 红色](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-light.png) #FF0000 | 合并文本和属性冲突     | 当两个或多个开发人员修改文件的相同行和相同的文件属性时，就会发生文本和属性冲突。 |
| ![颜色样本: 亮海军蓝](https://intellijidea.com.cn/help/img/idea/2023.2/modified-light.png) #0032A0 | 修改的                 | 自上次同步以来该文件已更改。                                 |
| ![颜色样本：蓝色](https://intellijidea.com.cn/help/img/idea/2023.2/modified-inactive-changelist-light.png) #0047E4 | 在非活动变更列表中修改 | 非活动更改列表中的文件已被修改。如果在“设置”\| “突出显示非活动更改列表中的文件”选项已启用，则此文件状态可用。版本控制 \| 变更列表。 |
| ![色样: 橄榄色](https://intellijidea.com.cn/help/img/idea/2023.2/obsolete-light.png) #7C7C00 | 过时的                 | 该文件不应再位于存储库的工作副本中。                         |
| ![颜色样本： 青色](https://intellijidea.com.cn/help/img/idea/2023.2/renamed-light.png) #007C7C | 更名                   | 自上次更新以来，该文件已被重命名。                           |
| ![颜色样本：深青色](https://intellijidea.com.cn/help/img/idea/2023.2/switched-light.png) #08978F | 已切换                 | [SVN] 该文件取自与整个项目不同的分支。                       |
| ![颜色样本： 棕色](https://intellijidea.com.cn/help/img/idea/2023.2/unversioned-light.png) #993300 | （未知）未版本化       | 该文件存在于本地，但不在存储库中，并且未计划添加。           |
| ![颜色样本： 黑色](https://intellijidea.com.cn/help/img/idea/2023.2/up-to-date-light.png)无（默认颜色） | 最新                   | 该文件尚未更改。                                             |

**达库拉主题**

| 颜色                                                         | 文件状态                          | 描述                                                         |
| ------------------------------------------------------------ | --------------------------------- | ------------------------------------------------------------ |
| ![Color sample: dull green](https://intellijidea.com.cn/help/img/idea/2023.2/added-darcula.png) #629755 | 添加                              | [活动变更列表](https://intellijidea.com.cn/help/idea/managing-changelists.html)中的文件计划添加到存储库中。 |
| ![Color sample: dull green](https://intellijidea.com.cn/help/img/idea/2023.2/added-darcula.png) #629755 | 添加到非活动变更列表中            | 非活动更改列表中的文件计划添加到存储库中。如果在“设置”\| “突出显示非活动更改列表中的文件”选项已启用，则此文件状态可用。版本控制 \| 变更列表。 |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-darcula.png) #D5756C | 变更列表冲突                      | 非活动变更列表中的文件已在活动变更列表中被修改。在这种情况下，将打开一个新对话框，提示您解决[更改列表冲突](https://intellijidea.com.cn/help/idea/resolving-conflicts.html)。如果在“设置”\|“设置”中启用了所有选项，则此文件状态可用。版本控制 \| 变更列表。 |
| ![Color sample: green](https://intellijidea.com.cn/help/img/idea/2023.2/copied-darcula.png) #0A7700 | 已复制                            | 如果一个文件是另一个文件的副本，则会跟踪其元数据，并将此类文件标记为已复制。 |
| ![Color sample: grey](https://intellijidea.com.cn/help/img/idea/2023.2/deleted-darcula.png) #6C6C6C | 已删除                            | 该文件计划从存储库中删除。                                   |
| ![Color sample: dull purple](https://intellijidea.com.cn/help/img/idea/2023.2/deleted-darcula.png) #6C6C6C | 从文件系统中删除                  | 该文件已在本地删除，但尚未计划删除，并且仍然存在于存储库中。 |
| ![Color sample: light blue](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-darcula.png) #6897BB | 改变了后代                        | 如果文件被修改，IDE 将递归突出显示包含该文件的所有目录。如果在“设置”\| “项目树”中启用“突出显示项目树中包含已修改文件的目录”选项，则此状态可用。版本控制 \| 确认。 |
| ![Color sample: light blue](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-darcula.png) #6897BB | 立即改变孩子                      | 如果文件被修改，IDE 将突出显示其父目录。如果在“设置”\| “项目树”中启用“突出显示项目树中包含已修改文件的目录”选项，则此状态可用。版本控制 \| 确认。 |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png)无（默认颜色） | 被劫持                            | [Perforce、ClearCase、VSS] 文件被[修改但未签出。](https://intellijidea.com.cn/help/idea/handling-modified-without-checkout-files.html) |
| ![Color sample: light olive](https://intellijidea.com.cn/help/img/idea/2023.2/ignored-darcula.png) #848504 | 被忽略                            | VCS 故意取消跟踪文件。                                       |
| ![Color sample: light purple](https://intellijidea.com.cn/help/img/idea/2023.2/merged-darcula.png) #9876AA | 合并                              | 作为更新的结果，该文件由您的 VCS 合并。                      |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-darcula.png) #D5756C | 与冲突合并                        | 在上次更新期间，该文件已合并并存在冲突。                     |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-darcula.png) #D5756C | 合并财产冲突                      | 在上次更新期间，IDE 检测到本地文件的属性与其服务器版本之间存在差异。 |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-darcula.png) #D5756C | 合并文本和属性冲突                | Text and property conflicts happen when two or more developers modify the same lines of a file and the same file properties. |
| ![Color sample: light blue](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-darcula.png) #6897BB | Modified                          | The file has changed since the last synchronization.         |
| ![Color sample: light blue](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-darcula.png) #6897BB | Modified in not active changelist | The file in an inactive changelist has been modified. This file status is available if the Highlight files from non-active changelists option is enabled in Settings \| Version Control \| Changelists. |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Obsolete                          | The file should no longer be in your working copy of the repository. |
| ![Color sample: strong cyan](https://intellijidea.com.cn/help/img/idea/2023.2/renamed-darcula.png) #3A8484 | Renamed                           | Since the last update, the file has been renamed.            |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Switched                          | [SVN] The file is taken from a different branch than the whole project. |
| ![Color sample: soft red](https://intellijidea.com.cn/help/img/idea/2023.2/unversioned-darcula.png) #D1675A | (Unknown) Unversioned             | The file exists locally but is not in the repository and is not scheduled for addition. |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Up to date                        | The file hasn't been changed.                                |

**高对比度主题**

| Color                                                        | File Status                             | Description                                                  |
| ------------------------------------------------------------ | --------------------------------------- | ------------------------------------------------------------ |
| ![Color sample: green](https://intellijidea.com.cn/help/img/idea/2023.2/added-hcontrast.png) #62CC47 | Added                                   | The file in the active [changelist](https://intellijidea.com.cn/help/idea/managing-changelists.html) is scheduled for addition to the repository. |
| ![Color sample: green](https://intellijidea.com.cn/help/img/idea/2023.2/added-hcontrast.png) #62CC47 | Added in not active changelist          | The file in an inactive changelist is scheduled for addition to the repository. This file status is available if the Highlight files from non-active changelists option is enabled in Settings \| Version Control \| Changelists. |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-hcontrast.png) #FF6666 | Changelist conflict                     | The file in an inactive changelist has been modified in the active changelist. In this case, a new dialog will open, prompting you to resolve the [changelist conflict](https://intellijidea.com.cn/help/idea/resolving-conflicts.html). This file status is available if all options are enabled in Settings \| Version Control \| Changelists. |
| ![Color sample: green](https://intellijidea.com.cn/help/img/idea/2023.2/added-hcontrast.png) #62CC47 | Copied                                  | If a file is a copy of another file, its metadata is tracked, and such a file is marked as copied. |
| ![Color sample: orange](https://intellijidea.com.cn/help/img/idea/2023.2/deleted-hcontrast.png) #ED864A | Deleted                                 | The file is scheduled for deletion from the repository.      |
| ![Color sample: orange](https://intellijidea.com.cn/help/img/idea/2023.2/deleted-hcontrast.png) #ED864A | Deleted from file system                | The file has been deleted locally but hasn't been scheduled for deletion, and it still exists in the repository. |
| ![Color sample: vivid cyan](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-hcontrast.png) #4FF0FF | Have changed descendants                | If a file is modified, the IDE will recursively highlight all directories containing that file. This status is available if the Highlight directories that contain modified files in the Project tree option is enabled in Settings \| Version Control \| Confirmation. |
| ![Color sample: vivid cyan](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-hcontrast.png) #4FF0FF | Have immediate changed children         | If a file is modified, the IDE will highlight its parent directory. This status is available if the Highlight directories that contain modified files in the Project tree option is enabled in Settings \| Version Control \| Confirmation. |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Hijacked                                | [Perforce, ClearCase, VSS] The file is [modified without checkout.](https://intellijidea.com.cn/help/idea/handling-modified-without-checkout-files.html) |
| ![Color sample: light olive](https://intellijidea.com.cn/help/img/idea/2023.2/ignored-hcontrast.png) #A9B837 | Ignored                                 | A file is intentionally untracked by VCS.                    |
| ![Color sample: light purple](https://intellijidea.com.cn/help/img/idea/2023.2/merged-hcontrast.png) #ED94FF | Merged                                  | The file is merged by your VCS as a result of an update.     |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-hcontrast.png) #FF6666 | Merged with conflicts                   | During the last update, the file has been merged with conflicts. |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-hcontrast.png) #FF6666 | Merged with property conflicts          | During the last update, the IDE has detected differences between the properties of the local file and its server version. |
| ![Color sample: dull red](https://intellijidea.com.cn/help/img/idea/2023.2/conflicts-hcontrast.png) #FF6666 | Merged with text and property conflicts | Text and property conflicts happen when two or more developers modify the same lines of a file and the same file properties. |
| ![Color sample: vivid cyan](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-hcontrast.png) #4FF0FF | Modified                                | The file has changed since the last synchronization.         |
| ![Color sample: vivid cyan](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-hcontrast.png) #4FF0FF | Modified in not active changelist       | The file in an inactive changelist has been modified. This file status is available if the Highlight files from non-active changelists option is enabled in Settings \| Version Control \| Changelists. |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Obsolete                                | The file should no longer be in your working copy of the repository. |
| ![Color sample: vivid cyan](https://intellijidea.com.cn/help/img/idea/2023.2/changed-descendants-hcontrast.png) #4FF0FF | Renamed                                 | Since the last update, the file has been renamed.            |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Switched                                | [SVN] The file is taken from a different branch than the whole project. |
| ![Color sample: soft red](https://intellijidea.com.cn/help/img/idea/2023.2/unversioned-darcula.png) D1675A | (Unknown) Unversioned                   | The file exists locally but is not in the repository and is not scheduled for addition. |
| ![Color sample: white](https://intellijidea.com.cn/help/img/idea/2023.2/hijacked-darcula.png) None (default color) | Up to date                              | The file hasn't been changed.                                |

> 本章介绍 VCS 文件状态颜色。如果您需要设置颜色来区分特定范围的项目文件，请参考[此页面](https://intellijidea.com.cn/help/idea/settings-file-colors.html)。

## 版本控制系统注释﻿

**1、什么是 VCS 注释？**﻿

注释是一种文件表示形式，显示每行代码的详细信息。特别是，对于每一行，您可以查看该行的起源版本、提交该行的人员的用户 ID 以及提交日期。带注释的视图可帮助您找出谁在何时做了什么，并追溯更改。

注释代码行可用于 ClearCase、Mercurial、Git、Perforce 和 Subversion。

“注释”命令可从版本控制菜单的 VCS 特定节点、编辑器装订线的上下文菜单、文件上下文菜单和文件[历史记录](https://intellijidea.com.cn/help/idea/viewing-changes-information.html#changes_history)视图中使用。

启用注释后，装订线看起来类似于以下示例：

![注释](https://intellijidea.com.cn/help/img/idea/2023.2/annotate.png)

当前版本中修改的行的注释用粗体和星号标记。

**2、启用注释**﻿

- 右键单击编辑器或[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)中的装订线，然后从上下文菜单中选择使用 Git Blame 进行注释。

  您可以为“注释”命令分配自定义快捷方式：转到IDE 设置的 “键盘映射”页面，然后查找“版本控制系统”|“版本控制系统”。git | git 注释。`Ctrl` `Alt` `S`

  要关闭注释，请右键单击编辑器或[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)中的装订线，然后从上下文菜单中选择“关闭注释” 。

**3、配置注释中显示的信息量**﻿

您可以选择要在注释视图中查看的信息量。

- 右键单击注释装订线，选择“查看”并选择要查看的信息类型，包括此更改源自的修订版、日期、不同格式的作者姓名以及提交号。

  您还可以在“颜色”下设置突出显示。

**4、配置注释选项**﻿

- 右键单击注释装订线并从上下文菜单中选择选项：
  - 忽略空格：空格将被忽略（git `blame -w`）。这意味着注释将指向先前有意义的提交。
  - 检测文件内的移动：当提交在同一文件中移动或复制行时，此类更改将被忽略（git `blame -M`）。这意味着注释将指向先前有意义的提交。
  - 检测跨文件的移动：当提交移动或复制在同一提交中修改的其他文件中的行时，此类更改将被忽略（git `blame -C`）。这意味着注释将指向先前有意义的提交。
  - 显示提交时间戳：如果您希望 IntelliJ IDEA 在注释视图中显示提交时间戳而不是创作更改的时间，请选择此选项。

**5、自定义日期格式**﻿

1. 按打开 IDE 设置，然后选择外观和行为 | 系统设置| 日期格式。`Ctrl` `Alt` `S`
2. 单击“VCS 注释”旁边的“日期时间模式”字段，并指定要用于 VCS 注释的日期格式。请参阅[模式参考](https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html)。

**6、注释以前的修订**﻿

IntelliJ IDEA 不仅允许您注释当前文件修订版本，还可以注释其先前的修订版本。注释装订线的上下文菜单提供以下选项：

- 注释修订：如果您想检查提交特定更改后文件的外观，此选项非常有用。为此，请右键单击此更改并从上下文菜单中选择注释修订。
- 注释以前的修订：如果您发现自己处于特定行中的最后更改毫无意义的情况（例如，如果所有更改都是代码格式），则此选项很有用。在这种情况下，您可以检查该文件的先前版本是什么样子。为此，请右键单击更改并从上下文菜单中选择“注释先前修订版” 。

[您还可以从文件历史](https://intellijidea.com.cn/help/idea/viewing-changes-information.html#changes_history)记录视图中注释特定文件。在“历史记录”选项卡中，选择要查看的文件版本，右键单击相应行并从上下文菜单中选择“注释” 。

**7、查看修订版本之间的差异**﻿

要查看文件的带注释版本与其先前版本之间的差异，请将脱字符号放在注释处，右键单击它，然后选择“显示差异”。IntelliJ IDEA 打开[文件的差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)：

![IntelliJ IDEA：差异查看器](https://intellijidea.com.cn/help/img/idea/2023.2/annotations_show_diff.png)

您还可以调用 VCS Operations 弹出窗口并选择Annotated Line | 显示差异。`Alt`

**8、导航至日志**﻿

如果您使用Git进行版本控制，还可以在 版本控制工具窗口 的 Log选项卡中从注释视图跳转到相应的提交。`Alt` `9`

为此，请将插入符号放在注释处，右键单击它，然后从上下文菜单中选择“在 Git 日志中选择” 。您还可以使用复制修订版本号命令在日志中查找修订版本。

[对于https://github.com/](https://github.com/)上托管的项目，还可以使用“在 GitHub 上打开”命令，将您带到相应的提交。



------



