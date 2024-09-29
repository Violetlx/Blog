---
title: IDEA 使用 Git 详解(二)
tags:
  - IDEA
categories:
  - 工具
description: IDEA 使用 Git 详解(二)
top_img: >-
  https://boosterminiclass.com/wp-content/uploads/2023/07/intellij_idea_git_2.png
cover: >-
  https://boosterminiclass.com/wp-content/uploads/2023/07/intellij_idea_git_2.png
date: '2024-09-25 14:45:03'
abbrlink: ae9ce5fc
---

![ https://n.sinaimg.cn/sinakd10116/612/w2000h1012/20200629/34e0-ivrxcex3246619.jpg](https://n.sinaimg.cn/sinakd10116/612/w2000h1012/20200629/34e0-ivrxcex3246619.jpg)

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

**2、检查项目文件状态**﻿

ntelliJ IDEA 允许您检查本地工作副本与项目的存储库版本相比的状态。它可以让您查看哪些文件已被修改、哪些新文件已添加到 Git 以及哪些文件未被 Git 跟踪。

打开 提交工具窗口。`Alt` `0`

![Git 文件状态](https://intellijidea.com.cn/help/img/idea/2023.2/Git_file_status.png)

- 更改更改列表显示自上次与远程存储库同步以来已修改的所有文件（以蓝色突出显示），以及已添加到 Git 但尚未提交的所有新文件（以绿色突出显示）。
- Unversioned Files更改列表显示已添加到项目中但 Git 未跟踪的所有文件。

> 如果您希望忽略的文件也显示在 “更改”视图中，请单击![查看选项](https://intellijidea.com.cn/help/img/idea/2023.2/app-client.expui.general.show.svg)工具栏上的 并选择“显示忽略的文件”。



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





































