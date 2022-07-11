# My code

`HashPassword`

```js
module.exports.hashPassword = (password) => {
    return new Promise((resolve,reject) => {
        bcrypt.hash(password,SALT_ROUNDS,(err,encrypted) => {
            if(err)
                return reject(err)
                
            resolve(encrypted)
        })
    })
}
```
`matchPassword`
```js
module.exports.matchPassword = (hash,password) => {
    return new Promise((resolve,reject) => {
        bcrypt.compare(password,hash,(err,same) => {
            if(err)
                return reject(err)
            resolve(same)
        })
    })
}
```

`StringUtil`
```js
module.exports.slugify = (title) => {
    let slugArr = []

    for(let i=0;i<title.length;i++){
        if(i>=30)
            break;

        let char = title[i].toLowerCase()
        if(char >= 'a' && char <= 'z')
            slugArr.push(char)
        else
            slugArr.push('-')
    }

    return slugArr.join('')
}
```

`jwt sign`

```js
module.exports.sign = async (user) => {
    const JWT_SECRET = "your-secret"
    return new Promise((resolve,reject) => {
        jwt.sign({
            username:user.username,
            email: user.email
        },JWT_SECRET,(err,token) => {
            if(err)
                return reject(err)
            return resolve(token)
        })
    })
    
}
```

`jwt decode`

```js
module.exports.decode = async (token) => {
    const JWT_SECRET = 'your secret'
    return new Promise((resolve,reject) => {
        jwt.verify(token,JWT_SECRET,(err,decoded) => {
            if(err)
                return reject(err)

            return resolve(decoded)
        })
    })
}
```