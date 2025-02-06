## Solve LinkedList Related Problem. 



At first we are going to learn about LinkedList Data Structures like how can we build LinkedList Data Structure and some basic operation about linkedList after that, we will some interview realted problms

---

### Singly LinkedList

**Create Node:**

```js
    class Node{
        constructor(value){
            this.val = value,
            this.next = null
        }
    }
```

Here we have successfully create a node means data set for linked list. Now we need to create a linkedList where every node will connect each and others in memory.

**Create a LinkedList:**
```js
    class LinkedList{
        constructor(value){
            let newNode = new Node(value)
            this.head = newNode
            this.tail = newNode
            this.length = 1
        }
    }

    let linkedList = new LinkedList(10)
```
Here i we have successfully create a linkedList. Now we are going to start inserting node to the linkedlist.

**Add Item at the beginning of the linkedlist.**
```js
    class LinkedList{
        constructor(value){
            let newNode = new Node(value)
            this.head = newNode
            this.tail = newNode
            this.length = 1
        }

        // add item to the begining of the linkedlist
        unshift(value){
            // edge case
            let newNode = new Node(value)
            if(!this.head){
                this.head = newNode
                this.tail = newNode
                this.length = 1
            }
        
           newNode.next = this.head
           this.head = newNode
           this.length += 1;
           return this
        }
    }
```

Now we are going to add node at the end of the linkedlist

**Here We have written rest of the operatin about linkedList:**

```js
    class LinkedList{
        constructor(value){
            let newNode = new Node(value)
            this.head = newNode
            this.tail = newNode
            this.length = 1
        }

        // add item to the begining of the linkedlist
        unshift(value){
            // edge case
            let newNode = new Node(value)
            if(!this.head){
                this.head = newNode
                this.tail = newNode
                this.length = 1
            }
        
           newNode.next = this.head
           this.head = newNode
           this.length += 1;
           return this
        }
        // add node at the end of the linkedlist
        push(value){
            let newNode = new Node(value)
            // check edge case
            if(!this.head){
                this.head = newNode
                this.tail = newNode
                this.length = 1
            }

            this.tail.next = newNode
            this.tail = newNode
            this.length += 1
            return this
        }

        // get node at specific index
        get(index){
            // check edge case
            if(index < 0  || index > this.length ) return undefined;

            let temp = this.head;

            for(let i = 0; i < index; i++){
                temp = temp.next
            }
            return temp
        }

         // set value to index
        set(index, value){
          // recive the get index the perform a loop and then set it
          let temp = this.get(index)
          while(temp){
            temp.val = value
            return true
          }
          return false
        }

        // insert node at specific index
        insert(index, value){
            // edge case
            if(index < 0 || index > this.length) return false
            if(index == 0) return this.unshift(value)
            if(index == this.length) return this.push(value)
            
            let newNode = new Node(value)
            // recieve the specific index
            let temp = this.get(index - 1)
            
            newNode.next = temp.next
            temp.next = newNode
            this.length += 1
            return true
        }
        
        // remove node at the beginning of the linkedList
        shift(){
        // check edge case
            if(!this.head || this.length == 0) return undefined
            
            let temp = this.head;
            this.head = this.head.next
            temp.next = null
            this.length -= 1
            
            // for one item
            if(this.length == 0)
            {
            this.tail = null
            }
            return temp
        }
    
      // remove node at the end of the linkedlist
    pop(){
        // edge case check
        if(!this.head || this.length == 0) return false
        let temp = this.head
        let prev = this.head
        
        // perform a while loop under the last pointer
        while(temp.next){
        prev = temp
        temp = temp.next
        }
        
        this.tail = prev
        this.tail.next = null
        this.length -= 1;
        
        // if linked lists does have one value then tail null ve null
        if(this.length == 0){
        this.head = null
        this.tail = null
        }
        return temp
    }

    // remove node at specific item
    remove(index){
        // edge case 
        if(index < 0 || index >= this.length) return undefined
        if(index == 0) return this.shift(index)
        if(index == this.length) return this.pop(index)
        
        // get the  spacific index
        let before = this.get(index - 1)
        let temp = before.next
        
        before.next = temp.next
        temp.next = null
        this.length -= 1
        return temp
    }

      // other methods
    // ______________
    getHead(){
        return this.head
    }
    
    getTail(){
        return this.tail
    }
    
    printList(){
        let temp = this.head
        while(temp !== null){
        console.log(temp.val)
        temp = temp.next
        }
        
    }

    
    getLength(){
    return this.length 
    }
    
    }
```

