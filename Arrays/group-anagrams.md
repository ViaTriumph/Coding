Question: [https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)
```kotlin
    fun groupAnagrams(strs: Array<String>): List<List<String>> {
        val map = hashMapOf<String, MutableList<String>>()
        val list = mutableListOf<List<String>>()
        for(str in strs){
            val sortedStr = String(str.toCharArray().apply{sort()})
            if(map.contains(sortedStr)){
                map[sortedStr]!!.add(str)
            }else{
                map[sortedStr] = mutableListOf(str)
            }
        }
        
        for(value in map.values){
            list.add(value.toList())
        }
        
        return list.toList()
    }
```
