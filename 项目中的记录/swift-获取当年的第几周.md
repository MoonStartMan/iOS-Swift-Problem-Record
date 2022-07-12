# swift-获取当年的第几周

``` swift

private func getWeek(date: Date) -> Int {
	guard let calendar = NSCalendar(identifier: NSCalendar.Identifier.gregorian) else {
		return 0
	}
  let components = calendar.components([.weekOfYear, .weekOfMonth, .weekday, .weekdayOrdinal], from: date)
  
  ///	今年的第几周
  if let weekOfYear = components.weekOfYear {
  	return weekOfYear
  }
  return 0
}

```

