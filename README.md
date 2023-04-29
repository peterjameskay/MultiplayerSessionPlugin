# Multiplayer Session Plugin
A UE Plugin for creating online multiplayer sessions. Just follow the read me instructions and your game can allow users to 
Host and Join sessions using their Steam account. This is open source, so feel free to contribute to make something better.

![](https://github.com/peterjameskay/MultiplayerSessionPlugin/blob/main/example_host_join.jpg)

## Steps to add Plugin

1. Clone this repository to your local system.
2. Create a `Plugins` folder (if you don't have one yet) in your directory for your project.
3. Add this folder to the `Plugins` folder.
4. Open your project.
5. Go to Edit>Plugins and search for `Online Subsystem Steam` and make sure you check the box `Enabled`.
6. Restart your project, it should ask you to build the modules for the plugin, hit `Yes`.
7. Go into the `Config` folder in your project directory.
8. Add this to the bottom of your DefaultEngine.ini file:
```
[/Script/Engine.GameEngine]
+NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="OnlineSubsystemSteam.SteamNetDriver",DriverClassNameFallback="OnlineSubsystemUtils.IpNetDriver")
 
[OnlineSubsystem]
DefaultPlatformService=Steam
 
[OnlineSubsystemSteam]
bEnabled=true
SteamDevAppId=480
bInitServerOnClient=true
 
[/Script/OnlineSubsystemSteam.SteamNetDriver]
NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
```
9. Save and close that and then add this to DefaultGame.ini:
```
[/Script/Engine.GameSession]
MaxPlayers=100
```
10. Save and close, then go into your editor to compile.
11. After that is finished, close Unreal Engine and your editor.
12. Delete `Binaries`, `Saved` and `Intermediate` folders from the main directory.
13. Delete `Binaries` and `Intermediate` from the `Plugins` folder.
14. Right click on the project file and click `Generate Project Files`.
15. Restart your project, it should ask you to build the modules for the plugin, hit `Yes`.

## Steps to use Plugin
1. In your `Content Drawer` click the `MultiplaterSessions Content` folder.
2. Double click the Widget Blueprint called `Menu`.
3. Take a look at any customizations you want to make.
4. When you're done, add it to your viewport by going into the level blueprint.
5. Add `Create Widget` from `BeginPlay`.
6. For the class select `WBP Menu`.
7. From that execution add the function after `Create Widget` called `Menu Setup`.
8. Set the parameters to your liking.

Enjoy!
