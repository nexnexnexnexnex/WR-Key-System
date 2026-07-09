
# Wilted Rose Key System
An easy to use key system for Roblox developers, featuring a clean, dark UI, key links, key saving, and much more

# So, how do I set it up?
Here's a simple but thorough guide on how to set up WR for your script.

## Step 1
Add this line to the top of your script:
```local WR = loadstring(game:HttpGet("link.added.soon"))()```

Now, you'll have the entire WR functions for you to use.

## Step 2
It is **heavily** recommended that you complete these steps to ensure a smooth user experience.

Add these to your script:
``WR:SetScriptName("YourScriptName") -- change to whatever you want, but it should 100% be set.``

```WR:SetKeyLinks({"www.keylink1.com", "www.keylink2.com"}) -- add your key links. Can be set to a string saying that the key can't be acquired through a link, or that the key is paid, etc. (This must be set to something, or the UI won't load at all)```

```WR:SetValidKeys({ [KeyName] = boolean }) -- Add your valid keys. The boolean must always be set. Set the bool to true.```

## Step 3: BindableEvents
Out of the box, WR comes with 5 BindableEvents:
```WR.OnKeyEntered (when the key is entered)
WR.OnKeyValid (when they key is valid)
WR.OnKeyInvalid (when the key is neither valid nor banned)
WR.OnKeyBanned (when they key is banned)
WR.UILoaded (after the key UI is created)
```

It is recommended to connect to all of these events. Here are a few examples:
### OnKeyEntered
```
WR.OnKeyEntered:Connect(function(Key)
       print("Key entered!")
       -- You could perform a validation check here, and not use OnKeyValid, but it's totally up to you. You could use this space to track how many times they've entered a key, or send a message through a webhook
end)
```

### OnKeyValid
```
WR.OnKeyValid:Connect(function(Key)
   print("Key is valid!")
   -- You could now load your actual script, or put it all here
   -- You could also send a message to a webhook containing the user's account info (Username, UserID etc)
end)
```
### OnKeyInvalid
```
WR.OnKeyInvalid:Connect(function()
   print("Key is invalid!")
   -- Honestly, I'm not really sure what you could do with this event.
   -- You could use it to track how many times an incorrect key was entered, and kick them if they reach the limit
end)
```

### OnKeyBanned
```
WR.OnKeyBanned:Connect(function()
   warn("Key is banned!")
   -- You could send a message to a webhook here if you like
end)
```

### UILoaded
```
WR.UILoaded:Connect(function()
  print("Key UI loaded!")
  -- This doesn't really serve a purpose
  -- But it was added for developer convenience
end)
```

## Step 4: Loading the UI
Now that you've completed all of the steps  above, call `WR:CreateKeyUI()`
This creates the UI with nothing else needed, and ensuring all of the above elements are added ensure the best experience for your users.

> [!CAUTION]
> `CreateKeyUI()` must ALWAYS be called right at the bottom to ensure it loads correctly

## Key saving
WR automatically saves keys upon validation, so you don't have to worry about this. It also creates the entire folder structure from scratch, so you don't have to worry about that either. You'll find saved keys at `Workspace > WRKeySystem > KeySaves > [ScriptName].wrkey`
Also, WR handles automatic key checking. If a user already has a valid saved key in their KeySaves folder, the entire key UI is skipped and `OnKeyValid` is fired. (That's why it's good to implement it)

### Note
This is **not**, by any means, the complete, final version of Wilted Rose. There will be many bug fixes and improvements to come. For now, happy scripting!! 
