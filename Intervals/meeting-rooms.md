Question: [https://leetcode.com/problems/meeting-rooms/](https://leetcode.com/problems/meeting-rooms/)
```kotlin
    fun canAttendMeetings(intervals: List<Interval?>): Boolean {
        var list = intervals.filterNotNull()
        val comparator = Comparator<Interval>{ a,b ->
            a.end - b.end
        }
        list = list.sortedWith(comparator)

        var meetingRooms = 0
        for(i in 0..list.size-1){
            if(i == 0){
                continue
            }
            if(list[i].start < list[i-1].end){
                return false
            }
        }

        return true
    }
```
