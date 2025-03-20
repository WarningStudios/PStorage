
Save score
```javascript
        var score = 17

        PStorage_saveKey(myId, "score", score)
```

Get score
```javascript
        var score = PStorage_getKey(myId, "score")

        var message = "Your saved score is "
        message += score
        message += "!"

        api.sendMessage(myId, score)
        /*
        Output: "Your saved score is 17!"
        */
```
Save Item
```javascript
        var sword = {name: "Stone Sword", amount: 1, attributes: {customDisplayName: "Cheap Sword",
                                                                  customDescription: "This is made from cheap messy stone!"}}
        PStorage_saveKey(myId, "cheap_sword", sword)

```
Get Item
```javascript
        var sword = PStorage_getKey(myId, "cheap_sword")

        api.sendMessage(myId, sword.attributes.customDisplayName)

        /*
        Output: "Cheap Sword"
        */
```
