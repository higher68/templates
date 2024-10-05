作成日時: {{date:YYYY年MM月DD日（ddd）hh:mm}}  


tags: #{{date:YYYY-MM}} #weekly  
ID : {{date:YYYYMMDDHHmm}}

今年の目標：  
- [[2024年12月にありたい姿（目標）]]

<%*
const oneDayInSec = 24 * 60 * 60
const weeklyStr = tp.file.title
// 週の最初の日をとってくる
// ref: https://momentjs.com/docs/#/parsing/string/
// NOTE: 1は月曜日になる
const weekFirstDay = moment(weeklyStr + "-1")
const weekFirstDayUnix = weekFirstDay.unix();
const weekBeforeUnix = moment.unix(weekFirstDayUnix - (7 * oneDayInSec))
const weekBeforeStr = weekBeforeUnix.format('gggg/gggg-[W]ww')

tR += '## 先週の来週よくするためのやつを読み直す\n'
tR += `![[weekly/${weekBeforeStr}## どうすれば来週はもっとよくなる？]]\n`

const weekDaysMeta = [...Array(7).keys()].map(n => {
	const diff = (n - 2) * oneDayInSec
	const day = moment.unix(weekFirstDayUnix + diff)
	return {
		dayString: day.format("YYYY-MM-DD"),
		dailyNotePath: day.format("YYYY/MM/YYYY-MM-DD")
	}})

tR += '## 今週の体調\n'
weekDaysMeta.map(weekDayMeta => {
	tR += weekDayMeta.dayString
	tR += "\n"
	tR += `![[daily/${weekDayMeta.dailyNotePath}#### 体調]]`
	tR += "\n"
})

tR += '## 今週のよかったこと総括\n'
weekDaysMeta.map(weekDayMeta => {
	tR += weekDayMeta.dayString
	tR += "\n"
	tR += `![[daily/${weekDayMeta.dailyNotePath}### よかったこと]]`
	tR += "\n"
})

tR += '## 今週の悪かったこと総括\n'
weekDaysMeta.map(weekDayMeta => {
	tR += weekDayMeta.dayString
	tR += "\n"
	tR += `![[daily/${weekDayMeta.dailyNotePath}### 悪かったこと]]`
	tR += "\n"
})

tR += '## 今週完了したこと\n'
weekDaysMeta.map(weekDayMeta => {
	tR += weekDayMeta.dayString
	tR += "\n"
	tR += `![[daily/${weekDayMeta.dailyNotePath}### 今日完了させたいこと]]`
	tR += "\n"
})

tR += '## 今週の学び\n'
weekDaysMeta.map(weekDayMeta => {
	tR += weekDayMeta.dayString
	tR += "\n"
	tR += `![[daily/${weekDayMeta.dailyNotePath}### 学び]]`
	tR += "\n"
})

tR += '## 来週完了させること\n'

tR += '### 先週の完了させたかったことを眺める\n'
tR += ``

tR += '## どうすれば来週はもっとよくなる？\n'
tR += `![[weekly/${weekBeforeStr}## 来週完了させること]]\n`

tR += '## 今週のつぶやき\n'
weekDaysMeta.map(weekDayMeta => {
	tR += weekDayMeta.dayString
	tR += "\n"
	tR += `![[daily/${weekDayMeta.dailyNotePath}## つぶやき]]`
	tR += "\n"
})




%>
