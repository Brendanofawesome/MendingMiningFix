# MendingFix

MendingFix is a client-side Fabric mod that prevents a Mending repair from
resetting a player's mining progress.

It addresses [MC-176559](https://bugs.mojang.com/browse/MC-176559), where
repairing a tool while mining can cause the current block-breaking progress to
be lost.

## Requirements

- Minecraft 26.3
- Fabric Loader 0.19.5 or newer
- Java 25 or newer

Because this mod changes client-side block-breaking behavior, it is a
client-only mod and does not need to be installed on a server.

## Server policy

MendingFix can technically allow faster mining by preserving progress that
would otherwise be reset when a tool is repaired. Before using it on a
multiplayer server, ask the server operator whether it is allowed. Some
servers may consider this behavior cheating or an unfair advantage.

## Installation

1. Install [Fabric Loader](https://fabricmc.net/use/installer/) for the
   supported Minecraft version.
2. Download the MendingFix JAR from the project's releases.
3. Place the JAR in the Minecraft `mods` directory.
4. Start Minecraft with the Fabric profile.


## How it works

Minecraft normally compares the complete item stack when deciding whether the
player is still mining the same target. Mending changes the tool's damage
component when it repairs durability, so that comparison can fail and mining
progress is reset.

MendingFix wraps that comparison in the client
`MultiPlayerGameMode.sameDestroyTarget` method and ignores differences in the
`DAMAGE` component. Other item components are still compared normally.

## License

MendingFix is licensed under the [MIT License](LICENSE).
