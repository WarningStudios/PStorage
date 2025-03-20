# PStorage
	Use this engine to save any data for players invisible in bloxd.io!

	This is an engine that can save any data in the bloxd.io moonstone chest.
	You are free to use this in your own lobby with any information like a board 
	or a message that shows that you use PStorageEngine by WarningStudios.

# IMPORTANT:
	If you use this in your world, you shouldn't place any moonstone chest or make 
 	others able to place them. PStorage uses it to save all data, so players could 
	reset or change them if they can access a moonstone chest.

# USE:
```javascript
	/*
	Save a value under a specific name.


	Parameters
		- playerId: The ID of the player who saves
		- key: A specific name to identify the value
		-	value: A value in any type
	
	Results
 		- null
	 
	Note that if a key existed before, it will be replaced.
	*/

	PStorage_saveKey(playerId: PlayerID, key: string, value: any)






	/*
	Get a value that was saved under a specific key.

	Parameters
		- playerId: The ID of the player who has saved the value
		- key: The key that identifies the saved value

	Results
 		- any type: value that was saved

	This doesn't change the value!
	*/

	PStorage_getKey(playerId, PlayerID, key: string)
 



	/*
	Clear all saved values

	Parameters
 		- playerId: The ID of the player whose values should be deleted

	Results
 		- null

	PStorage_clearAll(playerId: PlayerID)

	*/


```
Use the following scripts:




 # Scripts: Paste all the following code in the 'World Code' window (you'll reach it by the 'World Code'-Button in any code block)

```javascript
	function PStorage_saveKey(playerId, key, value)
	{
		try{
		oldStorageString = api.getMoonstoneChestItemSlot(playerId, 5).attributes.customDisplayName
		} 
		catch(error)
		{
		oldStorageString = "{}"
		}
		const newStorageString = __P__updateJSON(oldStorageString, key, value)
		attributes = {}
		attributes.customDisplayName = newStorageString
		api.setMoonstoneChestItemSlot(playerId, 5, "Chest", 1, attributes)
	}


	function PStorage_getKey(playerId, key)
	{
		try{
			storageString = api.getMoonstoneChestItemSlot(playerId, 5).attributes.customDisplayName
		}
		catch(error)
		{
			storageString = "{}"
		}
		const storage = __P__loadJSON(storageString)
		returnValue = storage[key]
		return returnValue
	}


	function PStorage_clearAll(playerId)
	{
	api.setMoonstoneChestItemSlot(playerId, 5, "Chest", 1, {customDisplayName: "{}"})
	}


	/*
	Note that the following functions are used in the program, dont use them in your own scripts. 
	But they are essential!!!
	*/

	function __P__loadJSON(savedString) 
	{
   		const obj = JSON.parse(savedString);
    		return obj;
	}


	function __P__updateJSON(jsonText, key, newValue) 
	{
    	const jsonObj = JSON.parse(jsonText);
    	jsonObj[key] = newValue;
    	return JSON.stringify(jsonObj, null, 2);
	}

```
