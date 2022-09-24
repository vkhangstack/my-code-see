# My code

`Count Vowels`

```js
/**
 * @function countVowels
 * @description Given a string of words or phrases, count the number of vowels.
 * @param {String} str - The input string
 * @return {Number} - The number of vowels
 * @example countVowels("ABCDE") => 2
 * @example countVowels("Hello") => 2
 */

const countVowels = (str) => {
  if (typeof str !== "string") {
    throw new TypeError("Input should be a string")
  }

  const vowelRegex = /[aeiou]/gi
  const vowelsArray = str.match(vowelRegex) || []

  return vowelsArray.length
}

export { countVowels }
```

`Validate Email`

```js
/**
 * Returns whether the given string is a valid email address or not.
 */
const validateEmail = (str) => {
  if (str === "" || str === null) {
    throw new TypeError("Email Address String Null or Empty.")
  }

  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(str)
}

export { validateEmail }
```

`formatPhoneNumber`

```js
/**
 * @description - function that takes 10 digits and returns a string of the formatted phone number e.g.: 1234567890 -> 123 456 7890
 * @param {string} phoneNumber
 * @returns {string} - Format to XXX XXX XXXX pattern
 */
const formatPhoneNumber = (phoneNumber) => {
  if (phoneNumber.length !== 10 || isNaN(phoneNumber)) {
    return "Invalid phone number."
  }
  let index = 0
  return "XXX XXX XXXX".replace(/X/g, () => phoneNumber[index++])
}

export default formatPhoneNumber
// console.log(formatPhoneNumber("1234567890))
```

`HashPassword`

```js
module.exports.hashPassword = (password) => {
  return new Promise((resolve, reject) => {
    bcrypt.hash(password, SALT_ROUNDS, (err, encrypted) => {
      if (err) return reject(err)

      resolve(encrypted)
    })
  })
}
```

`matchPassword`

```js
module.exports.matchPassword = (hash, password) => {
  return new Promise((resolve, reject) => {
    bcrypt.compare(password, hash, (err, same) => {
      if (err) return reject(err)
      resolve(same)
    })
  })
}
```

`StringUtil`

```js
module.exports.slugify = (title) => {
  let slugArr = []

  for (let i = 0; i < title.length; i++) {
    if (i >= 30) break

    let char = title[i].toLowerCase()
    if (char >= "a" && char <= "z") slugArr.push(char)
    else slugArr.push("-")
  }

  return slugArr.join("")
}
```

`jwt sign`

```js
module.exports.sign = async (user) => {
  const JWT_SECRET = "your-secret"
  return new Promise((resolve, reject) => {
    jwt.sign(
      {
        username: user.username,
        email: user.email,
      },
      JWT_SECRET,
      (err, token) => {
        if (err) return reject(err)
        return resolve(token)
      }
    )
  })
}
```

`jwt decode`

```js
module.exports.decode = async (token) => {
  const JWT_SECRET = "your secret"
  return new Promise((resolve, reject) => {
    jwt.verify(token, JWT_SECRET, (err, decoded) => {
      if (err) return reject(err)

      return resolve(decoded)
    })
  })
}
```

` sha256`

```js
async function sha256(message) {
  // encode as UTF-8
  const msgBuffer = new TextEncoder().encode(message)

  // hash the message
  const hashBuffer = await crypto.subtle.digest("SHA-256", msgBuffer)

  // convert ArrayBuffer to Array
  const hashArray = Array.from(new Uint8Array(hashBuffer))

  // convert bytes to hex string
  const hashHex = hashArray.map((b) => b.toString(16).padStart(2, "0")).join("")
  return hashHex
}
```
