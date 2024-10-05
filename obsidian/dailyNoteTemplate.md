{{date:YYYY年MM月DD日（ddd）hh:mm}}  

tags: #{{date:YYYY-MM}} #daily  
ID : {{date:YYYYMMDDHHmm}}

今年の目標：  
- [[2024年12月にありたい姿（目標）]]　

<%*
// https://momentjs.com/docs/#/displaying/fromnow/
const goalName = "AWS SCS-02"
// なんかわからんけどmonthが0オリジンでキモい
const now = moment([2024, 9, 29]).fromNow(true);
tR += `#### ${goalName}まで${now}`
%>
#### 天気
#### 体調
  - メンタル総括：
  - 不快な場所：
  - 痛い箇所：
  
- [[🌱好きなもの、こと、言葉]]
- [[ワーキングルール]]
  
ーーーーーーーーーーーーーーー  
## 【最初に書く】
### 今日完了させたいこと
- ルーチン
	- [ ] 瞑想
	- [ ] デスクトップ掃除
	- [ ] タスク洗い出し
	- [ ] カレンダー書く
	- [ ] 感謝とよかったところ書く(ブラウザの履歴見るの良さそう)
	- [ ] 自分の欠点について考える(一旦フリーライティングに書く)
	- 情報収集
		- [ ] 日経新聞読む => ざっと見て気になるの詳細読む
		- [ ] feedly読む => いい記事はweb clipperする
		- [ ] pocket読む(1記事)=>15分
	- [ ] 本読み(1章ずつ)=>15分
	- [ ] Trelloにカード追加
		- [ ] タスク
		- [ ] 記事ネタ
<%*
let dayCounter = 1
let lastDailyNoteDate = tp.date.now("YYYY/MM/YYYY-MM-DD", -dayCounter)
while (!(await tp.file.exists("daily/" + lastDailyNoteDate + ".md"))) {
	console.log(dayCounter)
	dayCounter++
	lastDailyNoteDate = tp.date.now("YYYY/MM/YYYY-MM-DD", -dayCounter)
	if (dayCounter >= 5) break
}787

let lastDailyNote = "daily/" + lastDailyNoteDate
const file = tp.file.find_tfile(lastDailyNote)
const content = await app.vault.read(file)
const sectionRegex = /### 今日完了させたいこと([\s\S]+?)(##|$)/;
const sectionMatch = content.match(sectionRegex);
const sectionContent = sectionMatch[1]
const sectionRegex2 = /- 非ルーチン\n([\s\S]+?)(- 副業|$)/;
const sectionMatch2 = sectionContent.match(sectionRegex2);
const sectionContent2 = sectionMatch2[1];
const uncheckedTasks = sectionContent2.match(/[ \t]*- \[ \] .+/gm); // 未完了のタスクを抽出
tR += "- 非ルーチン\n"
tR += uncheckedTasks ? uncheckedTasks.join("\n") :  "	- [ ] ";
const sectionRegex3 = /- 副業\n([\s\S]+?)$/;
const sectionMatch3 = sectionContent.match(sectionRegex3);
const sectionContent3 = sectionMatch3[1];
const uncheckedTasks3 = sectionContent3.match(/^[ \t]*- \[ \] .+/gm); // 未完了のタスクを抽出
tR += "\n- 副業\n"
tR += uncheckedTasks3 ? uncheckedTasks3.join("\n") : "	- [ ] ";
%>

## 【思いついたら書く】
### よかったこと
#### 感謝

### 悪かったこと
#### 欠点について考える

#### イライラしたら書く場所

### フリーライティング  
#### 設計考える場所

#### 今日の気になるニュース

## 【最後に書く】

### 学び

## つぶやき