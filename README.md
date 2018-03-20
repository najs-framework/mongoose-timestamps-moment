### Installation

```bash
npm install -s mongoose-timestamps-moment moment
```

### Usage

Replacing `setupTimestamp` in mongoose Schema.prototype

```
Schema.prototype.setupTimestamp = require('mongoose-timestamps-moment').setupTimestamp
```

After that you can set custom `now` value in unit test

```javascript
const Moment = require('moment')

describe('Custom "now" value', function() {
  it('can create in a specific date', async function() {
    const now = new Date(1988, 4, 16)
    Moment.now = () => now

    const model = new Model()
    await model.save()
    expect(model.createdAt).toEqual(now)
    expect(model.updatedAt).toEqual(now)
  })
})
```

### License

MIT @ Nhat Phan
