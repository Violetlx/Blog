---
title: IDEA 使用 Git 详解
tags:
  - 工具
categories:
  - 工具
description: IDEA 使用 Git 详解
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



# Git

Git 设置：**设置 | 版本控制 | git**

所需插件：Git（默认捆绑并启用）



## 为 Git 远程设置密码

每次与远程 Git 存储库交互时（例如，在 pull、update 或 push 操作期间），都需要授权。你可以将 IntelliJ IDEA 配置为记住你的密码。这样你就不必再每次需要授权时指定你的凭据了。

**配置密码策略**

> 1. 在**设置**对话框中，选择**外观和行为 | 系统设置 | 密码** 在左边。`Ctrl` `Alt` `S`
>
> 2. 选择你希望 IntelliJ IDEA 如何处理 Git 远程存储仓库的密码：
>
>    - **在本机钥匙串中：**选择此项可使用本机钥匙串来存储你的密码。此设置仅适用于 macOS 和 Linux。
>
>    - **在 KeePass 中：**选择此选项可使用[KeePass 密码管理器](http://keepass.info/)来存储您的密码。
>
>      当您使用KeePass 密码管理器时，将使用主密码来访问存储个人密码的文件。一旦 IntelliJ IDEA 记住您的密码，除非您需要访问密码数据库，否则它不会询问您的密码。在MasterPassword字段中输入将用于访问**c.kdbx**文件的密码。
>
>      您可以在“数据库”字段中更改**c.kdbx**文件的默认位置。
>
>      要导入**c.kdbx**文件，请单击并从下拉菜单中![设置图标](https://intellijidea.com.cn/help/img/idea/2023.2/icon_viewMode.png)选择“导入”![浏览按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.ellipsis.svg) ，或者单击并指定包含密码的本地文件的路径。
>
>      如果您想从数据库中删除现有密码，请选择“清除”。
>
>    - 重新启动后不保存，忘记密码：如果您希望在关闭 IntelliJ IDEA 后重置密码，请选择此选项。



## 设置 Git 存储库

当您[克隆](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#clone-repo)现有的 Git 存储库或[将现有项目置于 Git 版本控制之下时](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#put-existing-project-under-Git)，IntelliJ IDEA 会自动检测您的计算机上是否安装了 Git。如果 IDE 找不到 Git 可执行文件，则建议下载它。

IntelliJ IDEA 支持来自 Windows Subsystem for Linux 2 (WSL2) 的 Git，该子系统在[Windows 10 版本 2004](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004/)中提供。

如果 Windows 上未安装 Git，IntelliJ IDEA 会在 WSL 中搜索 Git 并从那里使用它。**此外，对于使用\ \wsl$**路径打开的项目，IntelliJ IDEA 会自动从 WSL 切换到 Git 。

如果您需要手动配置 IntelliJ IDEA 以从 WSL 使用 Git，请转到**版本控制** | IDE 设置的 **Git** 页面，单击Git 可执行文件路径字段中的浏览图标，然后通过路径选择 Git from WSL，例如。`Ctrl` `Alt` `S` `\wsl$` `\\wsl$\debian\usr\bin\git`



**1、从远程主机检出项目（git clone）**

IntelliJ IDEA 允许你签出（用 Git 术语来说，克隆）现有存储库并根据你下载的数据创建新项目。

> 1. 要开始克隆 Git 存储库，请执行以下操作之一：
>
>    - 如果版本控制集成已启用，请转至**Git | 克隆**。
>
>    - 如果尚未启用版本控制集成，请转至**VCS | 从版本控制获取**。
>
>      或者，转到**文件 | 新 | 来自版本控制的项目**。
>
>    - 如果当前没有打开的项目，请单击“**欢迎**”屏幕上的“**从 VCS 获取**”。
>
> 2. 在“**从版本控制获取**”对话框中，指定要克隆的远程存储库的 URL，或选择左侧的 VCS 托管服务之一。
>
>    如果您已经登录到所选的托管服务，完成后将建议您可以克隆的可用存储库列表。
>
>    ![从 GitHub 获取项目](https://intellijidea.com.cn/help/img/idea/2023.2/get-from-vc-git.png)
>
> 3. 单击“**克隆**”。如果要基于已克隆的源创建项目，请在确认对话框中单击“**是**” 。Git 根映射将自动设置为项目根目录。
>
>    如果您的项目包含[子模块](https://git-scm.com/book/en/v2/Git-Tools-Submodules)，它们也将被克隆并自动注册为项目根。
>
> 4. 在**信任和开放项目“<project_name>”中**？ [在项目安全对话框中](https://intellijidea.com.cn/help/idea/project-security.html)，选择您想要打开项目的方式：**信任项目或在安全模式下预览**。
>
> 5. 当您第一次导入或克隆项目时，IntelliJ IDEA 会对其进行分析。如果 IDE 检测到多个配置（例如 Eclipse 和 Gradle），它会提示您选择要使用的配置。
>
>    > 如果您要导入的项目使用构建工具，例如[Maven](https://intellijidea.com.cn/help/idea/maven-support.html)或[Gradle](https://intellijidea.com.cn/help/idea/gradle.html)，我们建议您选择构建工具配置。
>
>    选择必要的配置并单击“确定”。
>
>    ![提示您选择导入项目的方式的对话框](https://intellijidea.com.cn/help/img/idea/2023.2/import-from-providers.png)
>
>    IDE 根据您的选择预先配置项目。例如，如果您选择Gradle，IntelliJ IDEA 将执行其构建脚本、加载依赖项等。



**2、将现有项目置于 Git 版本控制之下**﻿

**①、将整个项目与单个 Git 存储库关联**﻿

> 1. 打开您想要放入 Git 下的项目。
>
> 2. 按打开**VCS 操作弹出窗口**并选择启用版本控制集成。`Alt` `~`
>
>    或者，转到 **VCS | 启用版本控制集成**。
>
> 3. 选择Git作为版本控制系统，然后单击“**确定**”。
>
>    然后，整个项目将与单个 Git 目录关联，因此无需将每个文件单独添加到 Git 目录。
>
> 4. 启用 VCS 集成后，IntelliJ IDEA 会询问您是否要通过 VCS 共享项目设置文件。您可以选择始终添加以与使用 IntelliJ IDEA 的其他存储库用户同步项目设置。
>
>    ![通知提示选择如何处理配置文件](https://intellijidea.com.cn/help/img/idea/2023.2/sharing-project-notification.png)
>
> > 如果VCS Operations 弹出窗口中没有可用的“启用版本控制集成”选项，则表示已为该项目启用了 Git 版本控制。

**②、将项目内的不同目录与不同的 Git 存储库关联**﻿

> 1. 打开您想要放入 Git 下的项目。
>
> 2. 前往**VCS | 创建 Git 存储库**。
>
> 3. 在打开的对话框中，指定将在其中创建新 Git 存储库的目录。
>
>    Git 不支持外部路径，因此如果您选择项目根目录之外的目录，请确保要创建存储库的文件夹也包含项目根目录。
>
> 4. 如果您要在项目结构内创建多个 Git 存储库，请对每个目录重复前面的步骤。

为项目[初始化 Git 存储库](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#put-existing-project-under-Git)后，您需要将项目文件添加到存储库。

**3、添加文件到本地存储库**﻿

> 1. 在 “**提交**”工具窗口中，展开“**未版本化文件**”节点。`Alt` `0`
>
> 2. 选择要添加到 Git 或整个更改列表的文件，然后按或从上下文菜单中选择“**添加到 VCS**” 。`Ctrl` `Alt` `A`
>
>    您还可以从“项目”工具窗口将文件添加到本地 Git 存储库：选择要添加的文件，然后按或选择“Git | Git”。从上下文菜单添加。`Ctrl` `Alt` `A`

在项目中启用 Git 集成时，IntelliJ IDEA 建议在 Git 下添加每个新创建的文件，即使它是从 IntelliJ IDEA 外部添加的。您可以在版本控制 |中更改此行为。IDE 设置的 确认页面。如果您希望某些文件始终保持未版本化，则可以[忽略它们](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#ignore-files)。`Ctrl` `Alt` `s`

> **如果您尝试添加.gitignore**列表中的文件，IntelliJ IDEA 将建议强制添加它。在确认对话框中单击“取消”只会取消强制添加忽略的文件 - 所有其他文件都将添加到 Git 存储库。

**4、从版本控制中排除文件（忽略）**﻿

有时您可能需要保留某些文件未版本化。这些可以是 VCS 管理文件、实用程序工件、备份副本等。您可以通过 IntelliJ IDEA 忽略文件，IDE 不会建议将它们添加到 Git 并将它们突出显示为忽略。

您只能忽略未版本化的文件，即您在未版本化文件更改列表中看到的文件。如果文件已[添加到 Git](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#add-new-files)但未[提交，您可以在](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html)“更改”视图中右键单击该文件 并选择“回滚”。

Git 允许您在两种配置文件中列出忽略的文件模式：

> - **.git /info /排除**文件。
>
>   此文件中列出的模式仅适用于存储库的本地副本。
>
>   当您初始化或签出 Git 存储库时，会自动创建此文件。
>
> - VCS 根目录及其子目录中的一个或多个**.gitignore文件。**
>
>   这些文件被签入存储库，以便整个团队都可以使用其中的忽略模式。因此，它是存储被忽略的文件模式的最常见位置。
>
>   如果VCS根目录下没有**.gitignore**文件，可以在Project工具窗口任意位置右键，选择New | 文件，然后在“新建文件”对话框中键入**.gitignore**。
>
>   > 要在 Windows 资源管理器中创建**.gitignore**文件，请创建一个名为 .gitignore 的文件**。**Windows 会自动将其重命名为**.gitignore**。

**5、将文件添加到 .gitignore 或 .git/info/exclude**﻿

> 1. 决定要使用哪种[类型的 Git 配置文件来忽略文件。](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#add-gitignore)如果有疑问，请使用**.gitignore**。
>
> 2. 在“更改”视图或“项目”工具窗口中找到要忽略的未版本控制的文件或文件夹 。[这些视图中的文件颜色](https://intellijidea.com.cn/help/idea/file-status-highlights.html)可帮助您识别文件的状态。
>
> 3. 右键单击所选内容并选择Git | 添加到 .gitignore或Git | 添加到 .git/info/exclude。
>
>    [这些视图中的文件颜色](https://intellijidea.com.cn/help/idea/file-status-highlights.html)可帮助您识别文件的状态。

如果需要按某种模式或类型排除文件，可以直接编辑`.gitignore`或文件。`.git/info/exclude`请参阅[.gitignore 模式格式](https://git-scm.com/docs/gitignore?origin_team=T0288D531)。

> 如果您希望[忽略的文件](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#ignore-files)也显示在 “更改”视图中，请单击![眼睛图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.show.svg)工具栏上的 并选择“显示忽略的文件”。

**6、添加远程存储库**﻿

如果您基于本地源[创建了 Git 存储库](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#put-existing-project-under-Git)，则需要添加远程存储库以便能够在 Git 项目上进行协作，并消除在本地存储整个代码库的风险。当您需要共享您的工作并从中提取数据以将其他贡献者所做的更改集成到本地存储库版本时，您可以将更改推送到[远程](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#push)存储[库](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#pull)。

如果您已[克隆远程 Git 存储库](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#clone-repo)（例如，从[GitHub](https://github.com/) ），则远程会自动配置，并且当您想要与其[同步](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html)时不必指定它。Git 为您克隆的远程服务器提供的默认名称是origin。

有关共享不同项目格式的项目设置的更多信息，请参阅 [通过 VCS 共享项目设置](https://intellijidea.com.cn/help/idea/configure-project-settings.html#share-project-through-vcs)。

**7、定义一个远程**﻿

> 1. 在任何 Git 托管上创建一个空存储库，例如[Bitbucket](https://bitbucket.org/)或[GitHub](https://github.com/)。您可以在 GitHub 上创建存储库，而无需离开 IntelliJ IDEA：请参阅[在 GitHub 上共享项目](https://intellijidea.com.cn/help/idea/manage-projects-hosted-on-github.html#share-on-GitHub)。
> 2. 当您准备好通过选择 Git |推送提交时，调用“推送”对话框 从主菜单按下，或按。`Ctrl` `Shift` `K`
> 3. 如果您到目前为止尚未添加任何遥控器，则会显示“定义远程”链接而不是遥控器名称。单击它以添加遥控器。
> 4. 在打开的对话框中，指定远程名称和托管它的 URL，然后单击“确定”。

**8、添加第二个遥控器**﻿

在某些情况下，您还需要添加第二个远程存储库。例如，如果您克隆了一个没有写访问权限的存储库，并且要将更改推送到您自己的原始项目[分支，这可能会很有用。](https://intellijidea.com.cn/help/idea/fork-github-projects.html#fork)另一个常见的情况是，您克隆了自己的存储库，这是其他人的项目分支，您需要与原始项目同步并从中获取更改。

> 1. 转到 Git | 管理遥控器。Git远程对话框将打开。
> 2. 单击工具栏上的“添加” 按钮或按。![添加](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.add.svg)`Alt` `Insert`
> 3. 在打开的对话框中，指定远程名称和 URL，然后单击“确定”。
>
> - 要编辑远程（例如，更改已克隆的原始项目的名称），请右键单击[Git 日志工具窗口的“分支”窗格](https://intellijidea.com.cn/help/idea/log-tab.html#BranchesPane)中的远程分支，然后从上下文菜单中选择“编辑远程” 。
>
>   您还可以通过单击遥控器的名称，从[推送对话框](https://intellijidea.com.cn/help/idea/push-dialog-mercurial-git.html)中编辑遥控器。
>
> - 要删除不再有效的存储库，请在[Git 日志工具窗口的“分支”窗格](https://intellijidea.com.cn/help/idea/log-tab.html#BranchesPane)中右键单击它，然后从上下文菜单中选择“删除远程” 。



## 将文件添加到 Git 并跟踪更改

**1、将文件添加到 Git**﻿

> 1. 打开 提交工具窗口。`Alt` `0`
> 2. 通过按或从上下文菜单中选择“添加到 VCS” ，将“无版本控制文件”更改列表中的任何文件置于版本控制之下。您可以添加整个更改列表或选择单独的文件。`Ctrl` `Alt` `A`

如果您已为项目启用 Git 集成，IntelliJ IDEA 建议将每个新创建的文件添加到版本控制下。您可以在“版本控制”| “设置”对话框中更改此行为。确认。如果您希望某些文件始终保持未版本化，您可以将 Git 配置为忽略它们。`Ctrl` `Alt` `s`

> 您还可以从项目工具窗口将文件添加到本地存储库。选择要添加的文件，然后按或选择Git | 从上下文菜单添加。`Ctrl` `Alt` `A`
>

**2、检查项目文件状态**﻿

ntelliJ IDEA 允许您检查本地工作副本与项目的存储库版本相比的状态。它可以让您查看哪些文件已被修改、哪些新文件已添加到 Git 以及哪些文件未被 Git 跟踪。

打开 提交工具窗口。`Alt` `0`

![Git 文件状态](https://intellijidea.com.cn/help/img/idea/2023.2/Git_file_status.png)

- 更改更改列表显示自上次与远程存储库同步以来已修改的所有文件（以蓝色突出显示），以及已添加到 Git 但尚未提交的所有新文件（以绿色突出显示）。
- Unversioned Files更改列表显示已添加到项目中但 Git 未跟踪的所有文件。

> 如果您希望忽略的文件也显示在 “更改”视图中，请单击![查看选项](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.show.svg)工具栏上的 并选择“显示忽略的文件”。
>



**3、在编辑器中跟踪文件的更改**

您还可以在编辑器中修改文件时跟踪文件的更改。所有更改均通过更改标记突出显示，这些标记出现在已修改行旁边的装订线中，并显示自上次[与存储库同步](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html)以来引入的更改类型。当您将更改提交到存储库时，更改标记就会消失。

您对文本所做的更改是用颜色编码的：

- ![新添加行的标记](https://intellijidea.com.cn/help/img/idea/2023.2/lineAddedMarker.png)已添加行。
- ![修改行的标记](https://intellijidea.com.cn/help/img/idea/2023.2/lineChangededMarker.png)线路改变了。
- ![已删除行的标记](https://intellijidea.com.cn/help/img/idea/2023.2/lineDeletedMarker.png)行已删除。

> 您可以在编辑器 |上自定义线路状态的默认颜色。配色方案| IDE 设置的 VCS页面。`Ctrl` `Alt` `s`
>
> 要禁用装订线中的 VCS 标记，请取消选择“版本控制”| “装订线”中的“突出显示装订线中已修改的行”选项。IDE 设置的 确认页面。`Ctrl` `Alt` `s`

您可以使用将鼠标悬停在更改标记上然后单击它时出现的工具栏来管理更改。工具栏与一个框架一起显示，该框架显示修改行的先前内容：

![修改后的线标记](https://intellijidea.com.cn/help/img/idea/2023.2/changeMarkerToolbar.png)

您可以通过单击回滚更改![恢复图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.vcs.revert.svg)，并通过单击探索当前行的当前版本和存储库版本之间的差异![显示差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.vcs.diff.svg)。要突出显示已更改的片段，请单击![突出显示按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.actions.highlighting.svg)。

您可以复制此弹出窗口内容的任何部分并将其粘贴到编辑器中，而不是恢复整个文件。



**4、从存储库中删除文件**

如果您删除受版本控制的文件，它仍然存在于存储库中，直到您提交更改为止。已删除的文件将放置在活动更改列表中并以灰色突出显示。

> 1. 在“项目”工具窗口中选择一个文件，然后按或从上下文菜单中选择“删除” 。`Delete`
>
> 2. 在打开的对话框中，您可以选择是要删除该文件而不搜索用途，还是通过选中“安全删除”选项来执行安全删除（以确保删除未使用的文件）。
>
>    如果发现任何用法，将弹出“检测到用法”对话框，列出它们。您可以在删除该文件之前查看这些用法并删除对此文件的引用。
>
> 3. 将更改提交到存储库。



## 与远程 Git 存储库同步（获取、拉取、更新）

[在通过将更改推送到上游来](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#push)共享工作结果之前，您需要与远程存储库同步以确保项目的本地副本是最新的。您可以通过以下方式之一执行此操作：[获取更改](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)、[拉取更改](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#pull)或[更新项目](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#update)。

Git分支弹出窗口指示分支是否有尚未获取的传入提交：

![传入提交指示器](https://intellijidea.com.cn/help/img/idea/2023.2/Git_branches_incoming_commits_indicator.png)

**1、获取更改**﻿

当您从上游获取更改时，自上次与远程存储库同步以来提交的所有新数据都会下载到本地副本中。这些新数据不会集成到您的本地文件中，并且更改不会应用于您的代码。

获取的更改存储为远程分支，这使您有机会在将它们与文件[合并之前查看它们。](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)由于fetch不会影响你本地的开发环境。这是获取远程存储库所有更改更新的安全方法。

有两种方法可以从上游获取更改：

- 选择Git | 在主菜单中获取。

- 或者，打开“分支”弹出窗口并单击![获取图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.expui.vcs.fetch.svg)右上角。

  ![在分支弹出窗口中获取图标](https://intellijidea.com.cn/help/img/idea/2023.2/VCS_fetch_from_branches_popup.png)

[观看此视频](https://youtu.be/tnz2I9rxrfk)可更好地了解 IDE 中如何执行获取操作。

**2、更新分支**﻿

如果您需要将特定分支与其远程跟踪分支同步，请使用更新。[这是获取](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)并随后将更改应用到所选分支的便捷快捷方式。

- 在“分支”弹出窗口或 版本控制工具窗口的“分支”窗格中，选择一个分支并从上下文菜单中选择“更新” 。

IntelliJ IDEA 将从远程分支中[提取](https://git-scm.com/docs/git-pull)更改，并将它们[变基](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)或[合并](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)到本地分支，具体取决于在设置|中选择的更新方法。版本控制 | 吉特.

**3、拉动变更**﻿

如果您需要从另一个分支而不是其远程跟踪分支获取对当前分支的更改，请使用pull。当您拉取时，您不仅下载新数据，还将其集成到项目的本地工作副本中。

> 1. 转到Git | 拉。“拉取更改”对话框打开：
>
>    ![拉动对话框](https://intellijidea.com.cn/help/img/idea/2023.2/git_pull_dialog.png)
>
> 2. 如果您有一个多存储库项目，则会出现一个附加下拉列表，供您选择存储库。
>
> 3. 如果您为项目定义了多个遥控器，请从列表中选择一个遥控器（默认情况下为`origin`）。
>
> 4. 选择要将更改拉取到当前签出的分支的分支。默认情况下，选择当前本地分支跟踪的远程分支。如果您指定不同的分支，IntelliJ IDEA 将记住您的选择并在将来默认显示该分支。
>
> 5. 如果您需要使用选项拉取，请单击“修改选项”并从以下选项中进行选择：
>
>    - `--rebase`：从远程分支[获取](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)更改后，IntelliJ IDEA 会将本地未推送的更改[重新设置](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#rebase-branch)为已获取的更改。
>    - `--ff-only`：只有可以快进时，合并才会被解决。
>    - `--no-ff`：在所有情况下都会创建合并提交，即使可以将合并解析为快进。
>    - `--squash`：将在当前分支之上创建包含所有拉取更改的单个提交。
>    - `--no-commit`：将执行合并，但不会创建合并提交，以便您可以在提交之前检查合并的结果。
>
>    有关`pull`选项的更多信息，请参阅https://git-scm.com/docs/git-pull。
>
> 6. 单击“拉动”。

**4、更新您的项目**﻿

如果您有多个项目根目录，或者希望每次与远程存储库同步时从所有分支获取更改，您可能会发现更新项目是更方便的选择。

当您执行更新操作时，IntelliJ IDEA会从所有项目根和分支中[获取](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#fetch)更改，并将跟踪的远程分支[合并](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)到本地工作副本中（相当于pull）。

> 如果您的项目包含[子模块](https://git-scm.com/book/en/v2/Git-Tools-Submodules)，并且它们位于分支上，它们也会自动更新。
>
> 如果子模块处于分离的 HEAD状态，IntelliJ IDEA 将调用`git submodule update`，这将检查根存储库中引用的提交。这意味着仅当根存储库中的子模块引用发生更改或添加新的子模块时才会执行更新。

1. 前往VCS | 更新项目或按。“更新项目”对话框打开。`Ctrl` `T`
2. 选择更新类型（此策略将应用于 Git 版本控制下的所有根）：
   - 将传入的更改合并到当前分支：选择此选项可在更新期间执行[合并。](http://schacon.github.io/git/git-merge.html)这相当于运行`git fetch`然后`git merge`, 或`git pull --no-rebase`。
   - 在传入更改之上对当前分支进行变基：选择此选项可在更新期间执行[变基。](http://schacon.github.io/git/git-rebase.html)这相当于运行`git fetch`然后`git rebase`，或者`git pull --rebase`（所有本地提交都将放在更新的上游头之上）。

如果您选择以后不显示“更新项目”对话框，然后想要稍后修改默认更新策略，请转到“版本控制”|“更新项目”对话框。IDE设置的 确认页面，在调用这些命令时显示选项对话框下选择更新，并在下次执行更新时修改更新策略。CtrlAlt0S

更新操作完成后，Git工具窗口 中将添加 [“更新信息”](https://intellijidea.com.cn/help/idea/version-control-tool-window-update-info-tab.html)选项卡。[它列出了自上次与远程同步以来所做的所有提交，并允许您以与“日志”选项卡](https://intellijidea.com.cn/help/idea/log-tab.html)中相同的方式查看更改。`Alt` `9`

> 如果您想查看自上次更新以来修改的所有文件的完整列表，请将插入符号放在提交列表中的任意位置，然后按。您可以禁用分组以查看平面列表：单击“更改的文件”窗格中的工具栏。`Ctrl` `A`![通过...分组](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.groupBy.svg)



## 提交更改并将其推送到 Git 存储库

> 配置提交选项：设置 | 版本控制 | 犯罪
>
> 提交工具窗口 `Alt` `0`
>
> 犯罪 `Ctrl` `K`
>
> 提交和推送`Ctrl` `Alt` `K`
>
> 推 `Ctrl` `shift` `K`

将[新文件添加到 Git 存储库](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#add-new-files)，或修改已在 Git 版本控制下的文件，并且您对它们的当前状态感到满意后，您可以共享您的工作结果。这涉及到在本地[提交](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#commit)它们以将存储库的快照记录到项目历史记录中，然后将它们[推](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#push)送到远程存储库以便其他人可以使用它们。

**1、设置您的 Git 用户名**﻿

Git 需要知道您的用户名才能将提交与身份关联起来。如果您尚未设置用户名，IntelliJ IDEA 将在您首次尝试提交更改时提示您指定用户名。

- 打开[终端](https://intellijidea.com.cn/help/idea/terminal-emulator.html)并执行以下命令之一：
  - 要为计算机上的每个 Git 存储库设置名称，请使用`$ git config --global user.name "John Smith"`
  - 要为单个存储库设置名称，请使用`$ git config user.name "John Smith"`

**2、在本地提交更改**﻿

> 1. 打开 位于左侧的垂直提交工具窗口：`Alt` `0`
>
>    ![提交工具窗口](https://intellijidea.com.cn/help/img/idea/2023.2/ij_VCS_commit_tool_window.png)
>
> 2. 当您的更改准备好提交时，选择相应的文件或整个更改列表。
>
>    如果按，将选择整个活动更改列表。`Ctrl` `K`
>
>    您还可以选择Unversioned Files节点下的文件 - IntelliJ IDEA 将一步暂存并提交这些文件。
>
> 3. 如果要将[本地更改附加到最新提交](https://intellijidea.com.cn/help/idea/edit-project-history.html#amend-commit)而不是创建单独的提交，请选择“修改”选项。
>
> 4. 输入提交消息。您可以单击![提交消息历史记录按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.vcs.history.svg)以从最近提交消息的列表中进行选择。
>
>    您还可以稍后在推送提交之前[编辑提交消息。](https://intellijidea.com.cn/help/idea/edit-project-history.html#reword-commit)
>
>    > 您可以在版本控制 |上自定义提交消息规则。IDE 设置的 提交页面。还有一个快速修复和重新格式化操作，可以换行长行或重新格式化消息。CtrlAlt0S
>    >
>    > 您还可以定义将用作默认提交消息的提交模板。指定要在**.txt**文件中使用的样板文本，并在终端中执行以下命令将其添加到 Git 配置中：`git config --local commit.template <path_to_template_file>`
>
> 5. 如果您需要执行提交检查、提交后将文件上传到服务器或使用高级选项提交，请单击![齿轮图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.gearPlain.svg)右下角的 ：
>
>    ![高级提交选项弹出窗口](https://intellijidea.com.cn/help/img/idea/2023.2/ij_VCS_advanced_commit_options.png)
>
>    可以使用以下选项：
>
>    - 作者：如果您要提交其他人所做的更改，您可以指定这些更改的作者。
>
>    - 签署提交：选择是否要签署提交以证明您要签入的更改是由您做出的，或者您对所提交的代码负责。
>
>      启用此选项后，将以下行自动添加到提交消息的末尾：签署人：<用户名>
>
>    - 在提交检查区域中，选择您希望 IntelliJ IDEA 在将所选文件提交到本地存储库时执行的操作。
>
>      可以使用以下选项：
>
>      - 重新格式化代码：根据[项目代码样式](https://intellijidea.com.cn/help/idea/settings-code-style.html)设置执行代码格式化。
>      - 重新排列代码：根据[偏好的排列规则](https://intellijidea.com.cn/help/idea/reformat-and-rearrange-code.html)重新排列您的代码。
>      - 优化导入：删除多余的导入语句。
>      - 分析代码：在提交修改的文件时分析它们。单击选择配置文件以选择IDE 将运行检查的检查[配置文件。](https://intellijidea.com.cn/help/idea/customizing-profiles.html)
>      - 检查 TODO (<过滤器名称>)：查看与指定过滤器匹配的[TODO 项。](https://intellijidea.com.cn/help/idea/using-todo.html)单击“配置”以选择[现有的 TODO 过滤器](https://intellijidea.com.cn/help/idea/using-todo.html)，或打开[TODO 设置页面](https://intellijidea.com.cn/help/idea/settings-todo.html)并定义要应用的新过滤器。
>      - 清理：批量应用代码清理检查中的快速修复。单击选择配置文件以选择IDE 将运行检查的[配置文件。](https://intellijidea.com.cn/help/idea/customizing-profiles.html)
>      - 运行测试：[运行测试作为提交检查](https://intellijidea.com.cn/help/idea/performing-tests.html#run-tests-after-commit)。单击运行测试附近的选择配置，然后选择要运行的配置。
>      - 更新版权：根据所选的版权配置文件 - 范围组合添加或更新版权声明。
>
>    - 在“提交后”区域中，您可以选择用于将提交的文件上传到本地或远程主机、已安装的磁盘或目录的[服务器](https://intellijidea.com.cn/help/idea/configuring-synchronization-with-a-remote-host.html)访问配置或[服务器组。](https://intellijidea.com.cn/help/idea/server-groups.html)有关更多信息，请参阅[部署您的应用程序](https://intellijidea.com.cn/help/idea/deploying-applications.html)。
>
>      可以使用以下选项：
>
>      - 运行工具：选择您希望 IntelliJ IDEA 在提交所选更改后启动的[外部工具。](https://intellijidea.com.cn/help/idea/configuring-third-party-tools.html)您可以从列表中选择一个工具，或者单击“浏览”按钮并在打开的[“外部工具”](https://intellijidea.com.cn/help/idea/settings-tools-external-tools.html)![浏览按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.ellipsis.svg)对话框中配置外部工具。
>
>      - 将文件上传到：选择[服务器访问配置](https://intellijidea.com.cn/help/idea/configuring-synchronization-with-a-remote-host.html)或[服务器组](https://intellijidea.com.cn/help/idea/server-groups.html)，用于将提交的文件上传到本地或远程主机、已安装的磁盘或目录。
>
>        - 要禁止上传，请选择None。
>        - 要将服务器配置添加到列表中，请单击![浏览按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.ellipsis.svg)并填写打开的“添加服务器”对话框中的必填字段。
>
>        仅当启用FTP/SFTP/WebDAV 连接插件时，该列表才可用。
>
>      - 始终使用选定的服务器或服务器组：始终将文件上传到选定的[服务器](https://intellijidea.com.cn/help/idea/configuring-synchronization-with-a-remote-host.html)或[服务器组](https://intellijidea.com.cn/help/idea/server-groups.html)。
>
>        仅当启用FTP/SFTP/WebDAV 连接插件时，该复选框才可用。
>
> 6. 准备就绪后，单击“提交”或“提交并推送”( ) 在提交后立即将更改推送到远程存储库。您将能够在将当前提交以及所有其他提交推送到远程之前查看它们。`Ctrl` `Alt` `K`

**3、提交文件的一部分**﻿

有时，当您进行与特定任务相关的更改时，您还会应用影响同一文件的其他不相关的代码修改。[将所有此类更改包含到一次提交中可能不是一个好的选择，因为审查、恢复](https://intellijidea.com.cn/help/idea/undo-changes.html#revert-commit)、[挑选](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#cherry-pick)它们等会更加困难。

IntelliJ IDEA 允许您通过以下方式之一单独提交此类更改：

- 在“提交更改”对话框中选择要包含在提交中的修改后的[代码块和行](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#select_chunks_in_commit_changes_dialog)，并将其他更改保留为待处理状态，以便稍后可以提交它们。

- 当您编辑代码时，将不同的代码块即时[放入不同的更改列表中，然后分别提交这些更改列表。](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#put_changes_into_different_changelists)

  > 您还可以创建一个新的更改列表并[使其处于活动状态](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#changelists)，然后您之后所做的所有更改都将落入该更改列表中，而您之前所做的任何修改都将保留在原处。

**4、选择要提交的块和特定行**﻿

> 1. 打开 提交工具窗口。`Alt` `0`
>
> 2. 要显示所选文件的存储库版本和本地版本之间的差异，请在 提交工具窗口中单击工具栏上的 或按。`Alt` `0`![差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)`Ctrl` `D`
>
> 3. 选中要提交的每个已修改或新添加的代码块旁边的复选框，并保留其他更改未选中：
>
>    ![部分提交对话框](https://intellijidea.com.cn/help/img/idea/2023.2/partial_commit_dialog.png)
>
>    > 您还可以从已修改块的上下文菜单中选择移动到另一个更改列表，以在可以单独提交的不同更改列表之间拆分更改。
>    >
>    > 要为此操作分配自定义快捷方式，请在IDE 设置的“ 键盘映射”页面上的“版本控制系统”下查找“将行移至另一个更改列表”操作。`Ctrl` `Alt` `s`
>
> 4. 如果您只想提交块中的特定行，请右键单击要包含的行，然后选择“ 拆分块”和“将所选行包含到提交中”。
>
>    ![IntelliJ IDEA：在上下文菜单中的提交中包含当前行的选项](https://intellijidea.com.cn/help/img/idea/2023.2/include_line_to_commit.png)
>
>    
>
>    或者，将鼠标悬停在装订线上，然后选择或清除要包含在提交中或从中排除的行旁边的复选框。
>
> 5. 单击“提交”。未选定的更改将保留在当前更改列表中，以便您可以单独提交它们。

**5、将更改放入不同的更改列表中**﻿

> 1. 当您在编辑器中对文件进行更改时，请单击装订线中相应的[更改标记。](https://intellijidea.com.cn/help/idea/adding-files-to-version-control.html#track_changes)
>
>    > 如果装订线中没有更改标记，请确保在编辑器 |装订线中启用突出显示装订线中修改的行选项。IDE 设置的 常规页面。`Ctrl` `Alt` `s`
>
> 2. 在出现的工具栏中，选择已修改代码块的目标变更列表（或创建新的变更列表）：
>
>    ![部分提交变更列表](https://intellijidea.com.cn/help/img/idea/2023.2/partial_commit_changelists.png)
>
> 3. 单独提交每个变更列表。

**6、使用 Git 暂存区提交更改**﻿

[如果您更习惯于提交](https://git-scm.com/docs/git-add)更改的暂存概念，而不是使用自动暂存修改文件的[更改列表](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#changelists)，请按 打开 IDE 设置并选择版本控制 | Git，然后选择启用暂存区域复选框。`Ctrl` `Alt` `s`

提交工具窗口现在如下所示：

![Git暂存区](https://intellijidea.com.cn/help/img/idea/2023.2/git_staging_area.png)

使用暂存区域可以让您轻松地分别提交对同一文件的更改（包括重叠更改），并查看哪些更改已经暂存，而无需从编辑器切换焦点。

> 当您从使用更改列表切换到 Git 暂存区域时，所有现有更改列表都会保存。您可以在两种模式之间切换，而不会丢失所做的更改。

**7、提交的阶段更改**﻿

1. 执行以下操作之一：

   - 要暂存整个文件，请在 “提交”工具窗口中选择该文件并单击其右侧的 或按。`Alt` `0`![添加按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.add.svg)`Ctrl` `Alt` `A`

     ![从“提交”工具窗口进入阶段](https://intellijidea.com.cn/help/img/idea/2023.2/git_stage_from_toolwindow.png)

   - 要暂存文件中的特定块，请在编辑器中单击已修改块旁边的装订线中的[更改标记，然后单击](https://intellijidea.com.cn/help/idea/adding-files-to-version-control.html#track_changes)暂存。

     ![编辑器的阶段更改](https://intellijidea.com.cn/help/img/idea/2023.2/git_stage_from_editor.png)

     暂存的更改（包括从 IntelliJ IDEA 外部暂存的更改）在编辑器中用边框形状的更改标记进行标记：

     ![用于分阶段更改的装订线标记](https://intellijidea.com.cn/help/img/idea/2023.2/git_staged_marker.png)

   - 要暂存粒度更改，例如单行而不是代码块，甚至是对单行的多个更改之一，请在“ 提交”工具窗口中，选择包含更改的文件，然后从上下文菜单中选择“比较 HEAD”、“暂存版本”和“本地版本”。`Alt` `0`

     这将打开一个三向[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)，其中左窗格显示存储库版本，右窗格显示本地版本，中央窗格是一个功能齐全的编辑器，您可以在其中进行想要暂存的更改。

     ![舞台交互变化](https://intellijidea.com.cn/help/img/idea/2023.2/git_stage_interactively.png)

2. [准备就绪后，按照本地提交更改](https://intellijidea.com.cn/help/idea/commit-and-push-changes.html#commit_tool_window)中所述提交更改。

**8、将更改推送到远程存储库**﻿

在推送更改之前，[请与远程同步](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html)并确保存储库的本地副本是最新的以避免冲突。

IntelliJ IDEA 允许您将更改从任何分支上传到其[跟踪分支](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches)或任何其他远程分支。

> 1. 执行以下操作之一：
>
>    - 要从当前分支推送更改，请按或选择 Git | 从主菜单推送。CtrlShift0K
>    - 要从任何具有远程分支的本地分支推送更改，请在“分支”弹出窗口中选择该分支，然后从操作列表中选择“推送” 。
>
>    “推送提交”对话框将打开，显示所有 Git 存储库（对于多存储库项目）并列出自上次推送以来在每个存储库的当前分支中进行的所有提交。
>
>    如果您的项目使用多个非同步控制的存储库，则默认情况下仅选择当前存储库（有关启用同步存储库控制的更多信息，请参阅[版本控制设置：Git](https://intellijidea.com.cn/help/idea/settings-version-control-git.html)）。
>
>    > 您可以按所选提交来显示额外信息，例如提交作者、时间、哈希值和提交消息。Ctrl0Q
>
> 2. 如果存储库中没有遥控器，则会显示“定义远程”链接。单击此链接并在打开的对话框中指定远程名称和 URL。它将被保存，您可以稍后通过 Git 进行编辑 | 管理远程（有关更多信息，请参阅[添加远程存储库](https://intellijidea.com.cn/help/idea/set-up-a-git-repository.html#add-remote)）。
>
> 3. 如果你想修改要推送的目标分支，可以点击分支名称。该标签会变成一个文本字段，您可以在其中键入现有分支名称或创建新分支。您还可以单击右下角的编辑所有目标链接来同时编辑所有分支名称。
>
>    请注意，您无法更改本地分支：将推送每个选定存储库的当前分支。
>
>    > 您还可以通过按所选元素的或切换到编辑模式。EnterF2
>
> 4. 如果您已经进行了一些提交但还不想推送到远程分支，请在Git工具窗口的“日志”选项卡中选择要推送的最后一个提交，然后从列表中选择“将所有内容推送到此处...”选项行动。
>
>    “推送提交”对话框将打开，显示直到所选提交哈希的所有提交。
>
> 5. 如果您想在推送更改之前预览更改，请选择所需的提交。右侧窗格显示所选提交中包含的更改。您可以使用工具栏按钮检查提交详细信息。
>
>    如果提交的作者与当前用户不同，则该提交将标有星号。
>
>    > ### 
>    >
>    > 
>    >
>    > 如果您选择整个存储库，所有提交的所有文件将在右窗格中列出。
>    >
>    > 如果在多次提交中修改了同一文件，则当您选择这些提交或整个存储库时，该文件只会列出一次，并且如果您为此文件调用[差异查看器，则所有更改都将被压缩在一起。](https://intellijidea.com.cn/help/idea/differences-viewer.html)
>
> 6. 准备好后单击“推送”按钮，然后从下拉菜单中选择要执行的操作：“推送”或“强制推送”（相当于`push --force-with-lease`）。
>
>    仅当当前分支未在受保护的分支字段中列出时（请参阅[版本控制设置：Git](https://intellijidea.com.cn/help/idea/settings-version-control-git.html)），这些选择选项才可用，否则，您只能执行该`push`操作。

**9、如果推送被拒绝，请更新您的工作副本**﻿

如果由于工作副本已过时而拒绝推送，IntelliJ IDEA 将显示“推送被拒绝”对话框，前提是未选择“设置”对话框的[Git 设置](https://intellijidea.com.cn/help/idea/settings-version-control-git.html)页面中的“如果当前分支的推送被拒绝则自动更新”选项。请执行下列操作：

> 1. 如果您的项目使用多个 Git 存储库，请指定要更新其中的哪个。如果您想要更新所有存储库，无论推送是否被拒绝，请选择更新所有存储库选项。如果清除此选项，则仅更新受影响的存储库。
>
> 2. 如果您希望 IntelliJ IDEA 在下次使用您在此对话框中选择的更新方法拒绝推送时静默应用更新过程，请选择记住更新方法选择并在将来静默更新选项。
>
>    离开此对话框后， “设置”对话框的[Git 设置](https://intellijidea.com.cn/help/idea/settings-version-control-git.html)页面中的“如果当前分支的推送被拒绝，则自动更新”复选框将被选中，并且应用的更新方法将成为默认方法。
>
>    要更改更新策略，请取消选择此选项以在下次当前分支的推送被拒绝时调用“推送被拒绝”对话框，应用不同的更新过程，然后再次选择“记住更新方法选择”选项。
>
> 3. 通过分别单击[“变基”](http://schacon.github.io/git/git-rebase.html)或“合并”按钮来选择更新方法（ “变基”或“[合并”）。](http://schacon.github.io/git/git-merge.html)

**10、什么时候需要使用强制推送？**﻿

当您运行push时，如果远程存储库中有您丢失的更改并且您将用存储库的本地副本覆盖，Git 将拒绝完成操作。通常，您需要执行[拉取](https://intellijidea.com.cn/help/idea/sync-with-a-remote-repository.html#pull)以与远程同步，然后再使用更改进行更新。

该`--force push`命令禁用此检查并允许您覆盖远程存储库，从而擦除其历史记录并导致数据丢失。在幕后，当您选择强制推送时，IntelliJ IDEA 会执行该`push --force-with-lease`操作，这是一个更安全的选项，可帮助您确保不会覆盖其他人的提交（有关推送选项的更多详细信息，请参阅[git Push ）。](https://git-scm.com/docs/git-push)

您可能仍需要执行的一种可能情况`--force push`是，您对推送的分支进行变基，然后想要将其推送到远程服务器。在这种情况下，当您尝试推送时，Git 将拒绝您的更改，因为远程引用不是本地引用的祖先。如果您在这种情况下执行拉取，您最终将得到分支的两个副本，然后需要合并它们。



## 比较文件和文件夹版本

IntelliJ IDEA 允许您检查文件/文件夹的两个修订版之间或其当前本地副本与存储库版本之间的差异。差异显示在差异查看器中。

**有关在差异查看器**中过滤、导航和应用更改的更多信息，请参阅[比较文件、文件夹和文本源](https://intellijidea.com.cn/help/idea/comparing-files-and-folders.html)。

**1、将修改后的文件与其 Git 存储库版本进行比较**﻿

> 1. 打开 提交工具窗口。Alt00
>
> 2. 在更改列表中找到所需的文件并执行以下操作之一：
>
>    - 右键单击该文件并选择Git | 显示差异。
>    - 选择文件并按。Ctrl0D
>    - 双击该文件。
>
> 3. 将打开差异视图，其中突出显示对文件的更改。
>
>    右窗格包含文件的修改版本。您可以在差异视图中对其进行编辑。
>
>    左窗格包含文件的初始版本。它是只读的。您可以单击![恢复](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.diff.applyNotConflictsLeft.svg)(恢复) 来撤消更改。

**2、将文件或文件夹的当前版本与同一 Git 分支中的版本进行比较**﻿

> 1. 在“项目”工具窗口中选择一个文件或文件夹，然后选择“Git | Git”。从上下文菜单中与修订版进行比较。
> 2. 从打开的对话框中选择要与当前文件或文件夹版本进行比较的修订版本。

**3、将文件或文件夹的当前版本与另一个 Git 分支进行比较**﻿

> 1. 在“项目”工具窗口中选择一个文件或文件夹，然后选择“Git | Git”。从上下文菜单中与分支进行比较。
> 2. 从打开的对话框中选择要与当前文件或文件夹版本进行比较的分支。



## 调查 Git 存储库中的更改

在IntelliJ IDEA中，您可以追溯项目中的所有更改>。这可以帮助您[找到任何更改的作者，查看](https://intellijidea.com.cn/help/idea/investigate-changes.html#annotate_blame)[文件版本](https://intellijidea.com.cn/help/idea/investigate-changes.html#file-history)或提交之间的差异，并在必要时[安全地回滚和撤消](https://intellijidea.com.cn/help/idea/undo-changes.html)更改。



**1、回顾项目历史**﻿

您可以查看对与指定过滤器匹配的项目源所做的所有更改。要查看项目历史记录，请打开 Git工具窗口 的 “日志”选项卡。它显示了提交给所有分支和远程存储库的所有更改 `Alt` `9`：

![日志视图](https://intellijidea.com.cn/help/img/idea/2023.2/git_log_view.png)

在多存储库项目中，左侧的彩色条纹指示所选提交属于哪个根（每个根都标有自己的颜色）。将鼠标悬停在彩色条纹上可调用显示根路径的提示：

![根路径](https://intellijidea.com.cn/help/img/idea/2023.2/log_root_path.png)



**2、浏览和搜索项目历史记录**﻿

- 通过输入完整的提交名称或消息或其片段、修订号或正则表达式来搜索提交列表。

- 按分支或最喜欢的分支、用户、日期和文件夹（或多根项目的根和文件夹）过滤提交。

- 单击工具栏上的“转到哈希/分支/标签” 图标，或按并指定提交哈希、[标签](https://intellijidea.com.cn/help/idea/use-tags-to-mark-specific-commits.html)或要跳转到的分支的名称（您将被带到该分支中的最新提交）。![去](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.find.svg)`Ctrl` `F`

- 单击箭头跳转到长分支中的下一个提交：

  ![跳转到下一个提交](https://intellijidea.com.cn/help/img/idea/2023.2/jumpToNextCommit.png)

- 按和键跳转到父/子提交。如果您在Git工具窗口 的“日志”选项卡 中混合了对不同存储库和多个分支的提交，这尤其有用 。`←` `→` `Alt` `9`

> - 按 将焦点切换到搜索字段。Ctrl0L
> - 为了避免来回设置过滤器，请单击![添加按钮](https://intellijidea.com.cn/help/img/idea/2023.2/app.general.add.svg)工具栏上的 来打开与您的过滤器匹配的新选项卡。
> - 要自定义日期格式，请转至设置 | 外观和行为| 系统设置| 日期格式。

有关 Git工具窗口 的 “日志”选项卡的更多信息，请参阅[“日志”选项卡](https://intellijidea.com.cn/help/idea/log-tab.html)。`Alt` `9`



**3、查看特定修订版的项目快照**﻿

IntelliJ IDEA 允许您在选定的修订版本中查看项目的状态。

> 1. 打开 Git工具窗口 并切换到“日志”选项卡。`Alt` `9`
> 2. 选择一个提交，然后从上下文菜单中选择“显示修订版本的存储库” 。

将打开“存储库”工具窗口，其中包含所选版本的项目快照。



**4、查看两次提交之间的差异**﻿

IntelliJ IDEA 允许您检查两次提交之间修改了哪些文件，而不必浏览两次提交之间的更改。

> - 在Git工具窗口 的 “日志”选项卡中选择任意两个提交 ，然后从上下文菜单中选择“比较版本” 。`Alt` `9`
>
>   将打开“更改”工具窗口，其中包含所选提交之间修改的文件列表。![显示差异图标](https://intellijidea.com.cn/help/img/idea/2023.2/devkit.icons.gutter.diff.svg)您可以通过单击或按 来查看任何文件的差异。`Ctrl` `D`



**5、查看文件历史记录**﻿

您可以查看对特定文件所做的所有更改，并查找每个版本中具体修改的内容。

> 1. 在任何视图（项目工具窗口、编辑器、 更改视图等）中选择必要的文件。
> 2. 选择Git | 从VCS主菜单或选择的上下文菜单显示历史记录。“历史记录”选项卡已添加到 Git工具窗口，显示所选文件的历史记录，并允许您查看和比较其修订版本。
> 3. 要确定特定修订版中引入了哪些更改，请在列表中选择它。在面板的右侧立即显示差异。
> 4. 要在专用差异查看器中查看整个文件的差异，请在列表中选择它，然后按或单击工具栏上的按钮。[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)将打开，显示此版本中的更改。`Ctrl` `D`![显示差异](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)



**6、查看本地和提交的文件版本之间的差异**

您可以检查提交的文件修订与其本地版本有何不同：

> 1. 打开 Git工具窗口 并切换到“日志”选项卡。`Alt` `9`
> 2. 选择您感兴趣的提交，然后在右侧窗格中选择文件。
> 3. 单击![显示差异](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)工具栏上的按钮。



**7、查看更改的合并方式**﻿

IntelliJ IDEA 允许您查看如何将更改[从一个分支合并到另一个分支](https://intellijidea.com.cn/help/idea/apply-changes-from-one-branch-to-another.html#merge)，以及在合并期间如何[解决冲突（如果有）：](https://intellijidea.com.cn/help/idea/resolve-conflicts.html)

> - 在 Git工具窗口 的 “日志”选项卡中，选择您感兴趣的合并提交。`Alt` `9`
>
>   - 如果在合并过程中未检测到并解决任何冲突，IntelliJ IDEA 将在“更改的文件”窗格中显示相应的消息，并建议检查源自父级的更改：
>
>     ![来自父母的改变](https://intellijidea.com.cn/help/img/idea/2023.2/vcs_log_changes_from_parents.png)
>
>     从节点之一选择所需的文件，然后单击工具栏上的“显示差异” 图标或按。[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)将显示两个面板的差异，允许您将当前版本与选定的父版本进行比较。![显示差异](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)`Ctrl` `D`
>
>   - 如果合并期间发生冲突，“更改的文件”窗格将显示合并有冲突的文件列表。
>
>     选择所需的文件，然后单击工具栏上的“显示差异” 图标或按。[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)将显示一个三面板差异，允许您将当前版本与其每个父版本进行比较，并查看冲突是如何解决的。![显示差异](https://intellijidea.com.cn/help/img/idea/2023.2/app.actions.diff.svg)`Ctrl` `D`



**8、找到代码作者（使用 Git Blame 进行注释）**﻿

您可以使用VCS 注释（对应于[git-blame](https://git-scm.com/docs/git-blame) ）找出谁对文件引入了哪些更改。带注释的视图显示了每行代码的详细信息：

![注释](https://intellijidea.com.cn/help/img/idea/2023.2/annotate.png)

当前版本中修改的行的注释用粗体和星号标记。

默认情况下，不同的提交以不同的颜色突出显示（请参阅[配置注释中显示的信息量](https://intellijidea.com.cn/help/idea/investigate-changes.html#configure-annotations)）。

从注释视图，您可以跳转到：

- Git工具窗口 的“日志”选项卡 中的相应提交 ：单击注释或将鼠标悬停在其上，然后单击弹出窗口中包含详细信息的提交哈希。`Alt` `9`

  ![弹出窗口，其中包含有关提交的详细信息](https://intellijidea.com.cn/help/img/idea/2023.2/git-blame-hover.png)

- 行的差异：将鼠标悬停在注释上。IDE 将突出显示该行以及相应提交的更改。

  ![线路差异](https://intellijidea.com.cn/help/img/idea/2023.2/git-blame-difference-in-lines.png)

- [https://github.com](https://github.com/)上的相应提交：使用Open on GitHub上下文菜单选项。

- 如果启用了[问题导航](https://intellijidea.com.cn/help/idea/handling-issues.html)，则错误跟踪系统中的相关问题：将鼠标悬停在注释上，然后单击问题链接（如果提交消息中包含该链接）

> **启用注释**﻿
>
> - 右键单击编辑器或[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)中的装订线，然后从上下文菜单中选择使用 Git Blame 进行注释。
>
>   您可以为“注释”命令分配自定义快捷方式：转到IDE 设置的 “键盘映射”页面，然后查找“版本控制系统”|“版本控制系统”。git | git 注释。CtrlAlt0S
>
>   要关闭注释，请右键单击编辑器或[差异查看器](https://intellijidea.com.cn/help/idea/differences-viewer.html)中的装订线，然后从上下文菜单中选择“关闭注释” 。

> **配置注释中显示的信息量**﻿
>
> 您可以选择要在注释视图中查看的信息量。
>
> - 右键单击注释装订线，选择“查看”并选择要查看的信息类型，包括此更改源自的修订版、日期、不同格式的作者姓名以及提交号。
>
>   您还可以在“颜色”下设置突出显示。

> **配置注释选项**﻿
>
> - 右键单击注释装订线并从上下文菜单中选择选项：
>   - 忽略空格：空格将被忽略（git `blame -w`）。这意味着注释将指向先前有意义的提交。
>   - 检测文件内的移动：当提交在同一文件中移动或复制行时，此类更改将被忽略（git `blame -M`）。这意味着注释将指向先前有意义的提交。
>   - 检测跨文件的移动：当提交移动或复制在同一提交中修改的其他文件中的行时，此类更改将被忽略（git `blame -C`）。这意味着注释将指向先前有意义的提交。
>   - 显示提交时间戳：如果您希望 IntelliJ IDEA 在注释视图中显示提交时间戳而不是创作更改的时间，请选择此选项。

> **自定义日期格式**﻿
>
> 1. 按打开 IDE 设置，然后选择外观和行为 | 系统设置| 日期格式。`Ctrl` `Alt` `S`
> 2. 单击“VCS 注释”旁边的“日期时间模式”字段，并指定要用于 VCS 注释的日期格式。请参阅[模式参考](https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html)。

> **在编辑器中显示更改的作者**﻿
>
> [您可以将编辑器配置为在嵌入提示](https://intellijidea.com.cn/help/idea/inlay-hints.html)中显示对元素（方法或类）的最后更改的作者。要打开它们：
>
> 1. 按打开 IDE 设置，然后选择编辑器 | 镶嵌提示| 代码愿景。CtrlAlt0S
>
> 2. 选择代码作者选项。
>
> 3. 选择显示作者姓名的位置：
>
>    - 在线顶部（默认）
>
>      ![代码视觉镶嵌提示 置顶](https://intellijidea.com.cn/help/img/idea/2023.2/annotate-inlay-hints-top-hl.png)
>
>    - 在右侧
>
>      ![代码视觉镶嵌提示右](https://intellijidea.com.cn/help/img/idea/2023.2/annotate-inlay-hints-right-hl.png)
>
> 启用此选项后，您可以单击编辑器中的作者姓名提示来打开带注释的视图。

> **隐藏更改的作者**﻿
>
> 要在编辑器中隐藏代码作者的姓名，请执行以下操作之一：
>
> - 打开编辑器 | 镶嵌提示| IDE 设置的 “代码视觉”页面并禁用“代码作者”选项。CtrlAlt0S
> - 右键单击编辑器中的作者姓名提示，然后选择Hide `Code Vision: Code Author` Inlay Hints。

**9、注释以前的修订**﻿

IntelliJ IDEA 不仅允许您注释当前文件修订版本，还可以注释其先前的修订版本。注释装订线的上下文菜单提供以下选项：

- 注释修订：如果您想检查提交特定更改后文件的外观，此选项非常有用。
- 注释以前的修订：如果您发现自己处于特定行中的最后更改毫无意义的情况（例如，如果所有更改都是代码格式），则此选项很有用。在这种情况下，您可以检查该文件的先前版本是什么样子。
- 隐藏修订：此选项有助于避免看到不相关或管理更改。这些通常是由低级迁移或格式化操作引入的。当这些更改影响整个根时，它们会在“注释”对话框中造成混乱，因此可能需要从视图和“注释”列中排除更改。“隐藏修订”操作允许您从注释结果中就地排除修订，并在编辑器和装订线中显示结果。可以使用相反的操作“恢复隐藏修订”来恢复排除的修订。有关隐藏修订的信息显示在编辑器顶部的通知面板中。还可以通过单击通知面板中的相应链接来恢复隐藏的修订。

您还可以从“历史记录”视图中注释特定文件。在“历史记录”选项卡中，选择要查看的文件版本，右键单击相应行并从上下文菜单中选择“注释” 。



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
>      如果您单击“强制签出”，您本地未提交的更改将被覆盖，并且您将丢失它们。
>
>      如果您单击Smart Checkout，IntelliJ IDEA 将[搁置](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#shelve)未提交的更改，检出所选分支，然后取消搁置更改。如果取消搁置操作期间发生冲突，系统将提示您合并更改。有关详细信息，请参阅[解决冲突](https://intellijidea.com.cn/help/idea/resolve-conflicts.html)。
>
>      > 如果您想使用[存储](https://intellijidea.com.cn/help/idea/work-on-several-features-simultaneously.html#stash)而不是搁置来清理工作副本，请转到版本控制| IDE 设置的 Git页面，然后在“清理工作树使用”设置下选择“搁置”。`Ctrl` `Alt` `S`
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
>      ![合并对话框](https://intellijidea.com.cn/help/img/idea/2023.2/merge_dialog.png)
>
>      选择要合并到当前分支的分支，单击“修改选项”并从以下选项中进行选择：
>
>      - `--no-ff`：在所有情况下都会创建合并提交，即使可以将合并解析为快进。
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
>      当变基在提交时停止时，IntelliJ IDEA 窗口的右下角会弹出一条通知，让您继续或中止变基：
>
>      ![变基状态通知](https://intellijidea.com.cn/help/img/idea/2023.2/continue_rebase_notification.png)
>
>      在继续变基之前，您可以使用上下文操作（例如Revert、Undo、Amend等）修改此提交。如果您不执行任何操作，则此提交将按原样应用。
>
>      如果您已关闭通知，请从主菜单中选择Git | 继续变基以恢复它。
>
>    - 重写提交消息：单击重写或双击提交并在打开的迷你编辑器中编辑文本。
>
>    - 将两个提交合并为一个：选择要合并到前一个提交中的提交，然后单击“Squash”或“Squash”按钮旁边的箭头，然后单击“Fixup”。
>
>      如果您单击Squash，默认情况下，来自两个提交的消息将被合并，因此，如果您不修改生成的提交消息，此操作将反映在分支历史记录中。
>
>      如果单击Fixup，则修复提交的提交消息将被丢弃，因此此更改将在分支历史记录中不可见。
>
>      在这两种情况下，您都可以在应用这些操作之一时打开的迷你编辑器中编辑提交消息。
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
>      当变基在提交时停止时，IntelliJ IDEA 窗口的右下角会弹出一条通知，让您继续或中止变基：
>
>      ![变基状态通知](https://intellijidea.com.cn/help/img/idea/2023.2/continue_rebase_notification.png)
>
>      在继续变基之前，您可以使用上下文操作（例如Revert、Undo、Amend等）修改此提交。如果您不执行任何操作，则此提交将按原样应用。
>
>      如果您已关闭通知，请从主菜单中选择Git | 继续变基以恢复它。
>
>    - 重写提交消息：单击重写或双击提交并在打开的迷你编辑器中编辑文本。
>
>    - 将两个提交合并为一个：选择要合并到前一个提交中的提交，然后单击“Squash”或“Squash”按钮旁边的箭头，然后单击“Fixup”。
>
>      如果您单击Squash，默认情况下，来自两个提交的消息将被合并，因此，如果您不修改生成的提交消息，此操作将反映在分支历史记录中。
>
>      如果单击Fixup，则修复提交的提交消息将被丢弃，因此此更改将在分支历史记录中不可见。
>
>      在这两种情况下，您都可以在应用这些操作之一时打开的迷你编辑器中编辑提交消息。
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



















