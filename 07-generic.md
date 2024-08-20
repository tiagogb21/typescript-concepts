```js
    /**
     * S => State
     * T => Type
     * K => Key
     * V => Value
     * E => Element
    */

   // Poderíamos estender:
   // function useState<T extends number | string> --> vai aceitar APENAS number ou string

   // Poderíamos passar um valor default:
   // function useState<T extends number | string = string> --> se um tipo não for passado, vai assumir que é do tipo string
   function useState<T>() {
        let state: T

        function get() {
            return state
        }

        function set(newValue: T) {
            state = newValue
        }

        return { get, set }
   }

    let newState = useState<string | number>();

    newState.set(123)
    newState.get()

    newState.set('abc')
    newState.get()
```