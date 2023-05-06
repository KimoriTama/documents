---
layout: default
title: 引擎设定的添加/编辑
---

## 以前的方法
<!-- 吉里吉里2 では、本体は TVPGetCommandDesc で得られる "|" 区切り(他の区切り文字もあり)の文字列を得て、それを元にエンジン設定の項目を表示していた。  
また、プラグインでは、コメント部に --has-option-- を入れて、GetOptionDesc 関数を公開し、その中で本体と同じ文字列フォーマットで設定の詳細を入れていた。  
リンカに /COMMENT: で --has-option-- を追加していたが、最近の Visual Studio では無視されるので、通常の方法ではこれを DLL バイナリに入れることは出来なくなっていた。 -->
吉里吉里2中，主体用TVPGetCommandDesc得到的 "|" 分隔（也有其他的分隔字符）的字符串，以此为基础显示引擎设定的项目。
另外，在插件中，在注释部分加入--has-option--，公有GetOptionDesc函数，其中以与本体相同的字符串格式加入设定的详细内容。
向链接器添加的/COMMENT：中添加了--has-option-- 但最近的Visual Studio忽略了它，因此通常无法将其放入DLL二进制文件中。
## 吉里吉里Z的方法
<!-- 吉里吉里Z では、設定項目のリストは JSON にし、ソースに埋め込むのではなくリソースに入れる方法に変更した。  
JSON の具体的なフォーマットは、ファイルを見ればだいたい分かるはず。  
本体の方はリソースの option_desc_ja.json を編集してもらえば反映されるのでいいとして、プラグイン側は少し注意が必要。  
リソースの種類は、TEXT で、ID は文字列 IDR_OPTION_DESC_JSON で DLL に格納する。  

具体的には *.rc ファイルに、以下のように記述してリソースに追加する。  
IDR_OPTION_DESC_JSON TEXT "option_desc_ja.json"

resource.h では、IDR_OPTION_DESC_JSON を定義しない。  
IDR_OPTION_DESC_JSON を定義するとリソース ID が数値で追加される。 -->
在吉里吉里Z中，设定项目的列表为JSON，不是嵌入到源码中而是变更为加入到资源中的方法。
JSON的具体格式，看了文件应该就大概知道了。
本体方面只要编辑资源的option_desc_ja.json就可以反映出来，插件方面需要稍微注意一下。
资源的类型是TEXT，ID是字符串IDR_OPTION_DESC_JSON，存储在DLL中。

具体来说，在*.rc文件中，如下格式，追加到资源中。
IDR_OPTION_DESC_JSON TEXT“option_desc_ja.json”

resource.h不定义IDR_OPTION_DESC_JSON。
定义IDR_OPTION_DESC_JSON时，以数字形式添加资源ID。
### JSON 格式
还没写……
