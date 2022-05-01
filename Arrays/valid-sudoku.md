Question: [https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)
```kotlin
    fun isValidSudoku(board: Array<CharArray>): Boolean {
        val row = Array(9){mutableSetOf<Char>()}
        val column = Array(9){mutableSetOf<Char>()}
        val grid = Array(9){mutableSetOf<Char>()}
        
        for(i in 0..board.size-1){
            for(j in 0..board.size-1){
                if(board[i][j] == '.'){
                    continue
                }
                if(row[i].contains(board[i][j]) 
                   || column[j].contains(board[i][j]) 
                   || grid[getGrid(i,j)].contains(board[i][j])
                  ){
                    return false
                }else{
                    row[i].add(board[i][j])
                    column[j].add(board[i][j])
                    grid[getGrid(i,j)].add(board[i][j])
                }
            }
        }
        
        return true
    }
    
    private fun getGrid(i: Int, j: Int): Int{
        return when{
            i < 3 && j < 3 -> 0
            i < 3 && j < 6 -> 1
            i < 3 && j < 9 -> 2
            i < 6 && j < 3 -> 3
            i < 6 && j < 6 -> 4
            i < 6 && j < 9 -> 5
            i < 9 && j < 3 -> 6
            i < 9 && j < 6 -> 7
            i < 9 && j < 9 -> 8
            else -> 0
        }
    }
```
