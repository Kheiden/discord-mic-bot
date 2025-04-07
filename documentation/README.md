# Bot creation and configuration

## Obtaining a bot token

You need to obtain a bot token to log into Discord's server.

1. Go to <https://discord.com/developers/applications> and click on "New
   Application".

2. Inside the settings panel of your new application, click on "Bot".

3. Create a new bot. When asked about permissions, simply leaving blank is
   enough.

4. Click on "Copy Token".

5. Create a new file named `token.txt` and paste your token inside that file.

## Inviting the bot to a Discord server

Note: You need to have the permission to invite a bot to the destination server.
If you don't have such a permission, the destination server **will not be
shown** in step 4. You can also ask an administrator who has such a permission
to help you invite your bot.

1. Go to <https://discord.com/developers/applications> and click on your already
   created application.

2. Click on "Copy Client ID".

3. Go to
   ```
   https://discord.com/oauth2/authorize?client_id=<CLIENT_ID>&permissions=3145728&scope=bot
   ```
   (Replace `<CLIENT_ID>` with your Client ID)

4. Choose your destination server. Then click "Authorize".

## Binary Build
After
```
uv run pyinstaller --paths=.venv/Lib/site-packages --icon=icon.ico dmb/__main__.py
Copy-Item -Path ".venv\Lib\site-packages\*" -Destination "dist\__main__\_internal" -Recurse
Copy-Item -Path "token.txt" -Destination "dist\__main__\token.txt"
Copy-Item -Path "icon.ico" -Destination "dist\__main__\_internal\icon.ico"
```

Remove extra cache files
```
python -Bc "import pathlib; [p.unlink() for p in pathlib.Path('.').rglob('*.py[co]')]"
python -Bc "import pathlib; [p.rmdir() for p in pathlib.Path('.').rglob('__pycache__')]"
```

## Release

Create a .7z file
Create a new Github release

## Remote Desktop

If using RDP to the source machine, make sure to NOT configure remote audio.

![Remote Desktop Protocol required configuration](documentation/rdp.png)
