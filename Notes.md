# Module 5 - Essential Javascript concepts I

# The World’s Most Annoying Cookie Consent

Topics we’ll cover:

- setTimeout
- element.style
- forms
- formData & .get()
- event.preventDefault
- CSS: row-reverse
- toggling classes
- ‘disabled’ attribute

- By changing the `position` property to `fixed` it allows you to fix the position of the specified div relative to the viewport
    - using `top bottom left right` and `margin`, you can position the div in the centre
    
    ![Untitled](https://user-images.githubusercontent.com/25359882/194774880-472b31bd-0f7c-411b-a91c-dac2c04bd965.png)

    

```jsx
setTimeout(function(){
	// place the code you want to execute 3000 seconds later
}, 3000)
```

```jsx
// targeting an element's style using element.style (JS)
const revealBtn = document.getElementById('reveal-btn')
const answer = document.getElementById('answer')

revealBtn.addEventListener('click', function(){
    answer.style.display = 'block'
})
```

- Forms
    - Getting input from users
    
    ```jsx
    // Examples of input fields
    <input type="text">
    <input type="email">
    <input type="password">
    <input type="submit">
    ```
    
    - input type submit vs html button
        - both work just fine but html button gives you more benefits like adding an image to it.
    - you can add the `required` attribute to the input tags if the user needs to fill it out
    - preventing default behaviour
    
    ```python
    const loginForm = document.getElementById('login-form')
    
    loginForm.addEventListener('submit', function(e){
        e.preventDefault()
    })
    ```
    
    - FormData
        - storing data from a form in an object
        - constructor functions require you to state the `new` keyword
        
        ```jsx
        FormData(formElement)
        
        // Example
        const loginForm = document.getElementById('login-form')
        
        loginForm.addEventListener('submit', function(e){
            e.preventDefault()
            
            const loginFormData = new FormData(loginForm)
            console.log(loginFormData)
        })
        ```
        
        - `FormData.get()`
            - this get method allows you to see what our object holds
            
            ```jsx
            const loginForm = document.getElementById('login-form')
            
            loginForm.addEventListener('submit', function(e){
                e.preventDefault()
                const loginFormData = new FormData(loginForm)
                
                const name = loginFormData.get('astronautName')
                console.log(name)
            ```
            
    
    - Disabling elements
        - controlling when elements are usable
        - disabled attribute can be used in the html tag you want disabled
            
            ```jsx
            <button id="cartBtn" disabled>Add to Cart 🛒</button>
            ```
            
    - `mouseenter` keyword for `addEventListener` can be used to trigger any events when the mouse hovers over the button.
    - `flex-direction: row-reverse`
        - this will allow you to change the order of elements
        
        ```jsx
        const sortBtn = document.getElementById('sort-btn')
        const container = document.getElementById('container')
                          
        sortBtn.addEventListener('click', function(){
            container.classList.toggle('reverse')
        })
        ```
        
        - this will toggle the class `reverse` onto the element with ID container anytime the button ‘Sort by Shade’ is clicked.
        
        ![Untitled 1](https://user-images.githubusercontent.com/25359882/194774906-f934ce73-347a-41d7-8bf0-40834e9f173c.png)

        
    
    - Accessibility
        - labels are really good for navigation. Especially for users that use screen readers to understand what each input is for. Eexample
            
            ```jsx
            <input 
            					type="email" 
            					name="email" 
            					placeholder="Enter your email"
            					aria-label="Email address" 
            					required/>
            
            ```
