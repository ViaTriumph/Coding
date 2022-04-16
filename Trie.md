Trie Data structure in kotlin

Node used in Trie

```kotlin:Node.kt
data class Node(
    private val children: MutableMap<Char, Node> = mutableMapOf<Char, Node>(),
    private var isWord: Boolean = false
){
    fun addChild(key: Char, node: Node){
        children[key] = node
    }
    
    fun getChild(key: Char): Node?{
        return children[key]
    }
    
    fun removeChild(key: Char){
        children.remove(key)
    }
    
    fun getChildrenSize() = children.size
    
    fun getChildren() = children.values
    
    fun setAsWord(){
        isWord = true
    }
    
   	fun removeAsWord(){
        isWord = false
    }
    
    fun isWord() = isWord
}
```

Trie class
```kotlin:Trie.kt
class Trie{
    private val root: Node = Node()
    
    fun insertIterative(word: String){
        var currentWord = root
        for(c in word){
            var child = currentWord.getChild(c)
            if(child == null){
                child = Node()
                currentWord.addChild(c, child)
            }
            currentWord = child
        }
        
        currentWord.setAsWord()
    }
    
    fun insert(word: String){
       insert(word, root, 0)
    }
    
    private fun insert(word: String, currentWord: Node, index: Int){
        if(index == word.length){
            currentWord.setAsWord()
            return 
        }
        
        val char = word[index]
        var child = currentWord.getChild(char)
        if(child == null){
            child = Node()
            currentWord.addChild(char, child)
        }
        
        insert(word, child, index + 1)
    }
    
    fun searchIterative(word: String): Boolean{
        var currentWord = root
        
        for(c in word){
           	val child = currentWord.getChild(c)
            if(child == null){
                return false
            }
            currentWord = child
        }
        
        return currentWord.isWord()
    }
    
    fun search(word: String): Boolean{
        return search(word, root, 0, false)
    }
    
    fun startsWith(prefix: String): Boolean{
        return search(prefix, root, 0, true)
    }
    
    private fun search(word: String, currentWord: Node, index: Int, prefixSearch: Boolean): Boolean{
        if(index == word.length){
            return if(prefixSearch) true else currentWord.isWord()
        }
        val child = currentWord.getChild(word[index])
        if(child == null){
            return false
        }
        
        return search(word, child, index + 1, prefixSearch)
    }
    
    fun searchWithWildCard(word: String, currentWord: Node, index: Int, wildCard: Char): Boolean{
        if(index == word.length){
            return currentWord.isWord()
        }
        
        val ch = word[index]
    
        if(ch == wildCard){
            for(child in currentWord.getChildren()){
                if(search(word, child, index + 1, false)){
                    return true
                }
            }
            return false
        }
        
        val child = currentWord.getChild(ch)
        
        if(child == null){
            return false
        }

        return search(word, child, index + 1, false)
        
    }
    
    fun delete(word: String){
        delete(word, root, 0)
    }
    
    private fun delete(word: String, currentWord: Node, index: Int): Boolean{
        if(index == word.length){
           
            if(!currentWord.isWord()){
                return false
            }
            
            currentWord.removeAsWord()
            return currentWord.getChildrenSize() == 0
        }
        
        val child = currentWord.getChild(word[index])
        if(child == null){
            return false
        }
        
        val shouldDeleteWord = delete(word, child, index + 1)
        
        if(shouldDeleteWord){

            currentWord.removeChild(word[index])
            
            return currentWord.getChildrenSize() == 0
        }
        
        return false
    }
    
    fun getLexicographicSortedWords(): List<String>{
        val list = mutableListOf<String>()
        preOrder(root, "", list)
        return list.toList()
    }
    
    private fun preOrder(node: Node, str: String, list: MutableList<String>){
        if(node.isWord()){
            list.add(str)
        }
        var cStr = str
        for(i in 32..126){
            val ch = i.toChar()
            val child = node.getChild(ch)
            if(child == null){
                continue
            }
            preOrder(child, cStr + ch, list)
        }
    }
}
```

Try it out!
```kotlin:Main.kt
fun main() {
    val str = "lexicographic sorting of a set of keys can be accomplished with " +
                "a simple trie based algorithm we insert all keys in a trie output " +
                "all keys in the trie by means of preorder traversal which results " +
                "in output that is in lexicographically increasing order preorder " +
                "traversal is a kind of depth first traversal"
    val words = str.split(" ")
    
    val trie = Trie()
    

    for(word in words){
        trie.insert(word)
    }
    
    trie.delete("lexicographically")
    
    val sorted = trie.getLexicographicSortedWords()
    println(sorted.joinToString("\n"))
    
}
```
