# 投票

## 使用方法

投票组件可以帮助收集结果， 由投票发起人决定最后的投票结果。我们的投票组件仅仅帮助简化这个统计过程。 用户可以做许多设置自定义配置，如果由任何关于配置的疑问，可以参考 config.ts and defaultConfig.ts [跳转](/app/component/vote).

### 发起投票

当用户想要对某个议题发起投票时，可以新开一个issue。用户可以在issue body里面描述需要相关背景，然后，在下面的评论区发起一个开始投票的命令，格式如下：
`/start-vote a,b,c,d replier,commiter 3d`

- `start-vote` 该命令被定义在hypertrons的配置文件里，用户可以根据需要进行更改。
- `a,b,c,d` 这是4个候选项，需要使用逗号隔开.
- `replier,commiter`. replier 和 commiter 某种角色名，这个也可以在hypertrons的配置文件里找到。该项声明里哪些角色的用户拥有投票权利。这里支持多种用户角色，只要符合其中任意一种就具有参与投票的权利。注意多角色需要使用逗号隔开。
- `3d` 该项是指从发起投票到投票结束截止时间的持续时间。比如，3d就意味着，从发起投票开始计时，3天后投票自动过期，未参与投票者被视为自动放弃。目前我们支持两种格式，一种是按小时计(h)，一种是按天计(d)。

不用担心你会输入错误，因为我们提供了参数检查。输入错误，会给出对应提示，您可以根据提示进行修改，参数正确会收到成功提醒。

### 参与投票

`/vote a`

- `vote` 该命令被定义在hypertrons的配置文件里，用户可以根据需要进行更改。
- `a` 用户的选择。参与投票者可以在投票截止前不断更新自己的选择，投票组件底层只会记录最新的选择。投票者会在投票完成后立即收到是否投票成功的反馈。 

除了拼写错误，以及参数合法性检查，我们还会检查该用户是否具有投票权限，以及该投票是否过期。注意，投票组件底层由一个定时检查器，会关闭所有过期的投票活动。

## 实现原理

- 当lua投票组件在一个issue的评论区收到 `start-vote` 命令的时候, 我们会首先检查是否合法，然后把投票信息以json格式的形式存储到该issue的body里面，我们把这个称为元信息。人们看不到这部分信息，原因是这部分内容藏在了markdown注释里面。
- 当lua投票组件在一个issue的评论区收到 `vote` 命令的时候，我们主要会检查拼写错误，以及参数合法性检查，我们还会检查该用户是否具有投票权限。然后把这个信息同步到统计区域。
- 投票组件底层由一个定时检查器，会关闭所有过期的投票活动，并打上 `vote end` 的标签。

[源代码](/app/component/vote).

## 局限性

投票组件目前只支持github，如果你在 gitlab 或 gitee 遇到问题，不要太惊讶。欢迎屏幕前的你贡献代码！

## 相关资源

之前关于投票的讨论在[Issue#199](https://github.com/hypertrons/hypertrons/issues/199)，代码在[PR#207](https://github.com/hypertrons/hypertrons/pull/207).
