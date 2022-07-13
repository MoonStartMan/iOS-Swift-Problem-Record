# swift-NSCalendar

## Identifier的范围

``` objective-C

NSCalendarIdentifierGregorian         公历
NSCalendarIdentifierBuddhist          佛教日历
NSCalendarIdentifierChinese           中国农历
NSCalendarIdentifierHebrew            希伯来日历
NSCalendarIdentifierIslamic           伊斯兰日历
NSCalendarIdentifierIslamicCivil      伊斯兰教日历
NSCalendarIdentifierJapanese          日本日历
NSCalendarIdentifierRepublicOfChina   中华民国日历（台湾）
NSCalendarIdentifierPersian           波斯历
NSCalendarIdentifierIndian            印度日历
NSCalendarIdentifierISO8601           ISO8601

```

## 日历的设置

``` swift

let calendar = NSCalendar(identifier: NSCalendar.Identifier.gregorian)

```

## 日历信息的获取

``` swift

NSCalendarUnitEra                 -- 纪元单位。对于 NSGregorianCalendar (公历)来说，只有公元前(BC)和公元(AD)；而对于其它历法可能有很多，例如日本和历是以每一代君王统治来做计算。
NSCalendarUnitYear                -- 年单位。值很大，相当于经历了多少年，未来多少年。
NSCalendarUnitMonth               -- 月单位。范围为1-12
NSCalendarUnitDay                 -- 天单位。范围为1-31
NSCalendarUnitHour                -- 小时单位。范围为0-24
NSCalendarUnitMinute              -- 分钟单位。范围为0-60
NSCalendarUnitSecond              -- 秒单位。范围为0-60
NSCalendarUnitWeekOfMonth / NSCalendarUnitWeekOfYear -- 周单位。范围为1-53
NSCalendarUnitWeekday             -- 星期单位，每周的7天。范围为1-7
NSCalendarUnitWeekdayOrdinal      -- 没完全搞清楚
NSCalendarUnitQuarter             -- 几刻钟，也就是15分钟。范围为1-4
NSCalendarUnitWeekOfMonth         -- 月包含的周数。最多为6个周
NSCalendarUnitWeekOfYear          -- 年包含的周数。最多为53个周

```