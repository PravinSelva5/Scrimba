# Pumpkin’s Purrfect Meme Picker

![Untitled](Module%205%20-%20Essential%20Javascript%20concepts%20II%20ee81c615815048bbbf8a70d5cb0f0553/Untitled.png)

- During this project, you’ll get familar with:
    - `for of`
        - a nicer way of iterating through a list of objects
        
         
        
        ```jsx
        // Array of objects
        const characters = [
            {
                title: 'Ninja',
                emoji: '🥷',
                powers: ['agility', 'stealth', 'aggression'],
            },
            {
                title: 'Sorcerer',
                emoji: '🧙',
                powers: ['magic', 'invisibility', 'necromancy'],
            },
            {
                title: 'Ogre',
                emoji: '👹',
                powers: ['power', 'stamina', 'shapeshifting'],
            },
            {
                title: 'Unicorn',
                emoji: '🦄',
                powers: [ 'flight', 'power', 'purity'],
            }
        ]
        
        // for of example
        // 1. the console.log will output each object within characters
        for (let character of characters){
            console.log(character)
        }
        
        // 2.
        for (let character of characters){
            for (let power of character.powers){
                console.log(power)
            }
        /* Output:
        ›agility
        ›stealth
        ›aggression
        ›magic
        ›invisibility
        ›necromancy
        ›power
        ›stamina
        ›shapeshifting
        ›flight
        ›power
        ›purity
        */
        
        ```
        
    - radio inputs
        - Radio inputs gives users a choice of options
        
        ```jsx
        <div class="radios" id="radios">
        				<div class="radio">
        					<input 
        					type="radio"
        					id="horses"
        					value="horses"
        					name="choice-radios"
        					>
        					<label for="horses">5 duck-sized horses</label>
                        	<!-- radio here -->
        				</div>
        				<div class="radio">
                        	<!-- radio here -->
        				</div>
        				<button>Submit</button>
                    </div>
        ```
        
        ![Untitled](Module%205%20-%20Essential%20Javascript%20concepts%20II%20ee81c615815048bbbf8a70d5cb0f0553/Untitled%201.png)
        
    - import/export
        - import and export is useful when working with mulitple files
        
        ```jsx
        // in data.js file
        // export keyword is used to allow access to dinnerPartyGuests in another file
        export const dinnerPartyGuests = [
            'Elvis Presley', 
            'The Queen of England',
            'Alan Turing', 
            'Nelson Mandela', 
            'Mahatma Gandhi', 
            'Aristotle',
            'Albert Einstein'
            ]
        ```
        
        ```jsx
        // in index.js, it is importing the array of objects from data.js
        // you need to specify the object in brackets and include which file
        import { dinnerPartyGuests } from '/data.js'
        
        console.log(dinnerPartyGuests)
        ```
        
    - .includes()
        - this is a method for checking if an array holds a given value
    - .filter()
    - event.target.id
        - this allows you to check where the user clicked
        - an event (e), can be any interaction on the browser. Could be a click, double click, scrolling, etc.
            
            ```jsx
            const container = document.getElementById('container')
            
            const products = [
                {
                    name: 'Ostrich Pillow',
                    price: '10',
                    image: 'ostrichpillow.jpg',
                    id: 'ostrich-pillow'
                },
                {
                    name: 'Bacon Bandages',
                    price: '8',
                    image: 'bacon-bandage.jpg',
                    id: 'bacon-bandages'
                },
                {
                    name: 'Baby Mop',
                    price: '20',
                    image: 'babymop.jpg',
                    id: 'baby-mop'
                }
            ]
            
            let productsHtml = ``
            
            for (let product of products){
                productsHtml += `
                <div class="product">
                    <h3>${product.name}</h3>
                     <h4> £${product.price}</h4>
                    <img src="${product.image}">
                    <button id="${product.id}">Buy Now</button>
                </div>
                `
            }
            container.innerHTML = productsHtml
            
            container.addEventListener('click', function(e){
                console.log(e.target.id)
            })
            ```
            
    - .parentElement
        - this is used to access the parent element when the child element is known using an event listener
        
        ```jsx
        container.innerHTML = productsHtml
        
        container.addEventListener('click', function(e){
            document.getElementById(e.target.id).parentElement.style.backgroundColor = 'lightblue'
        })
        ```
        
        ![Untitled](Module%205%20-%20Essential%20Javascript%20concepts%20II%20ee81c615815048bbbf8a70d5cb0f0553/Untitled%202.png)
        
    - Updating the classList
        
        ```jsx
        document.addEventListener('click', function(e){
            document.getElementById(e.target.id).parentElement.classList.add('read')
            document.getElementById(e.target.id).parentElement.classList.remove('unread')
        })
        ```
        
        ![Untitled](Module%205%20-%20Essential%20Javascript%20concepts%20II%20ee81c615815048bbbf8a70d5cb0f0553/Untitled%203.png)
        
    - getElementsByClassName
        - this method allows you to grab all the elements with a given class
        
        ```jsx
        clearBtn.addEventListener('click', function(){
            const productsArray = document.getElementsByClassName('product')
            for (let product of productsArray){
                product.classList.remove('purchased')
                product.classList.add('on-offer')
                
            }
        })
        ```
        
        - When user clicks ‘CLEAR ALL’, opacity class is removed and cleared
        
        ![Untitled](Module%205%20-%20Essential%20Javascript%20concepts%20II%20ee81c615815048bbbf8a70d5cb0f0553/Untitled%204.png)
        
    - querySelector
        - this is a more powerful way of grabbing elements
        - in this example snippet, instead of looking for a specific ID or class, you can search for a specific input type
        
        ```jsx
        
        submitBtn.addEventListener('click', function(){
            const checkedRadio = document.querySelector('input[type="radio"]:checked')
            console.log(checkedRadio)
        })
        ```
        
    - Checkboxes
        
        ```jsx
        <div class="checkbox-container">
                        <div>
                            <label for="accept-terms">
                                I accept these terms and conditions
                            </label>
                            <input type="checkbox" id="accept-terms">
                        </div>
                        <div>
        ```
        
    - filter()
        - this method allows you to choose which elements you want from an array
        
        ```jsx
         const ages = [1, 5, 9, 23, 56, 10, 47, 70, 10, 19, 23, 18]
        
        const adults = ages.filter(function(age){
            if (age >= 18){
                return true
            }
            else {
                return false
            }
        })
        
        console.log(adults) // output --> [23, 56, 47, 70, 19, 23, 18]
        ```
        
        ```jsx
        // cleaner version of the above
        
        const ages = [1, 5, 9, 23, 56, 10, 47, 70, 10, 19, 23, 18]
        
        const adults = ages.filter(function(age){
            return age >= 18
        })
        
        console.log(adults)
        ```
