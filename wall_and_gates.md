```kotlin
// link: https://www.lintcode.com/problem/663/

class Solution {
    /**
     * @param rooms: m x n 2D grid
     * @return: nothing
     */
    fun wallsAndGates(rooms: Array<IntArray>): Unit {

        for(i in 0..rooms.size-1){
            for(j in 0..rooms[0].size-1){
                if(rooms[i][j] == 0){
                    dfs(rooms, i, j,0)
                }
            }
        }

    }

    fun dfs(rooms: Array<IntArray>, i: Int, j: Int, depth: Int){

        if(depth > rooms[i][j]){
            return
        }

        rooms[i][j] = depth

        if(i-1 >= 0 && rooms[i-1][j] != -1){
            dfs(rooms, i-1, j, depth + 1)
        }

        if(j-1 >= 0 && rooms[i][j-1] != -1){
            dfs(rooms, i, j-1, depth + 1)
        }

        if(i+1 < rooms.size && rooms[i+1][j] != -1){
            dfs(rooms, i+1, j, depth + 1)
        }

        if(j+1 < rooms[0].size && rooms[i][j+1] != -1){
            dfs(rooms, i, j+1, depth + 1)
        }
    }
}
```
