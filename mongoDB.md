1.difference between `mongoose.SchemaType` and `mongoose.Types.xx-type-name`:

```javascript
import mongoose from 'mongoose'

const schema = new mongoose.Schema({ name: { type: String } })
//or：
//const schema = new mongoose.Schema({ name: String });
schema.path('name') instanceof mongoose.SchemaType // true
schema.path('name') instanceof mongoose.Schema.Types.String // true
schema.path('name').instance // 'String'
```

2.difference between `mongoose.ObjectId` and `mongoose.Types.ObjectId`

- **both can be used** for declaring paths in your **schema** that should be [MongoDB ObjectIds](https://www.mongodb.com/docs/manual/reference/method/ObjectId/), but **only be instanceof** `mongoose.ObjectId`;
- **can only use `mongoose.Types.ObjectId`** to create a new ObjectId **instance**.

ps:

- 'ObjectId' in `mongoose.Types.ObjectId` is a kind of type typically used for unique identifiers.
  - It is **object**, but often represented as **string**.
  - You can use `toString()` converting an **object** 'ObjectId' to a 24-character hexadecimal **string**.

```javascript
/*01.used in schema*/
//(1)use `mongoose.ObjectId`
const carSchema = new mongoose.Schema(
  { driver: mongoose.ObjectId } //`used in schema`
)
typeof carSchema.path('driver') // 'object'
carSchema.path('driver') instanceof mongoose.ObjectId // true!
carSchema.path('driver') instanceof mongoose.Types.ObjectId // false
carSchema.path('driver').toString() // [object Object]

//(2)use `mongoose.Types.ObjectId`
const carSchema = new mongoose.Schema(
  { driver: mongoose.Types.ObjectId } //`used in schema`
)
typeof carSchema.path('driver') // 'object'
carSchema.path('driver') instanceof mongoose.ObjectId // true!!
carSchema.path('driver') instanceof mongoose.Types.ObjectId // false
carSchema.path('driver').toString() // [object Object]

/*02.used in instance*/
const carSchema = new mongoose.Schema(
  { driver: mongoose.ObjectId } //`used in schema`
)
const Car = mongoose.model('Car', carSchema)

const car = new Car()
car.driver = new mongoose.Types.ObjectId() //`used in instance`

typeof car.driver // 'object'
car.driver instanceof mongoose.ObjectId // false
car.driver instanceof mongoose.Types.ObjectId // true
car.driver.toString() // Something like "5e1a0651741b255ddda996c4"
```
