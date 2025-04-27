# CREATE VR App Documentation

Authored by: Jacob Stolker ([erifyc1](https://github.com/erifyc1))
Last Updated: `4/27/2025`

## Contents

#### [**I. Setup**](#Setup)

1. Environment
2. Headset
3. Building
4. Running

#### [**II. App Overview**](#App-Overview)

1. App descriptions
2. Development status

#### [**III. Packages**](#Packages)

1. Unity features
2. Packages
3. Asset store

#### [**IV. Asset Reference**](#Asset-Reference)

1. Scenes
2. Prefabs
3. Scripts

#### [**V. Future Directions**](#Future-Directions)

1. Bugs
2. Planned features

#### [**VI. Development Timeline**](#Development-Timeline)

1. Developers
2. Key design decisions
3. History

## Setup

#### Environment Setup

1. Install [Unity Hub](https://unity.com/unity-hub) and current editor version (2022.3.10f1)
2. Install [Visual Studio](https://visualstudio.microsoft.com/vs/unity-tools/) and make sure to add C#/Unity dev tools
3. Clone the repository
   `git clone <project_name.git>`
4. In Unity Hub, choose `Add -> Add project from disk`
5. Make sure the Unity Editor version is correct before launching

#### Headset Setup

1. If headset is new, follow Meta's setup guidelines
2. Once paired and connected to a phone, enable **Developer Mode** in the headset's settings.
    - If this option is not available, your account may need additional steps to be allowed to use developer mode. This might include accepting terms, adding a payment method, confirming a phone number, etc.

#### Building the App

1. In the **Unity Editor**, go to `File -> Build Settings`
2. In **Build Settings**, ensure all wanted scenes are included in the build. (Index 0 is the entrypoint scene)
3. Ensure **Android** is selected within the **Platform** section.
    - If this option is not selected, select it and hit **Switch Platform** at the bottom.
    - If this option is not available, you need to install **Android Build Tools**. There should be an option to install provided.
4. Ensure **Android** build options are configured correctly:
    - **Texture Compression**: ASTC
    - **ETC2 fallback**: 32-bit
    - **Export Project**: disabled
    - **Symlink Sources**: disabled
    - **Build App Bundle**: disabled
    - **Create symbols.zip**: disabled
    - **Run Device**: skip for now
    - **Development Build**: enabled
    - **Autoconnect Profiler**: disabled
    - **Deep Profiling Support**: disabled
    - **Script Debugging**: disabled
    - **Compression Method**: LZ4
5. Connect **VR Headset** via USB/USB-c.
    - Use rear/USB3.0+ ports if possible
    - Make sure cable is plugged into headset and not the extended battery. (you need to unplug this)
6. Click **Refresh** next to **Run Device** and select your headset in the dropdown.
    - If it does not show, try a different USB port. If this does not work, ensure **Developer Mode** is enabled for the headset. (see [Headset Setup](#Headset-Setup))
7. Click **Patch** or **Patch and Run** if the option allows. (**Patch and Run** builds and launches the app for you)
    - If the option fails due to a file/directory conflict, it means you need to choose a place for the build to go before it's uploaded to the headset. Choose **Build** at the bottom and specify a folder somewhere **outside the project repo** for the builds to be sent. Then, patch to the headset.
    - If the option to **Patch** is not available, follow the steps described in the previous bullet point.

#### Running the App

Note: These steps are likely to change due to constant UI updates. Custom apps do not show up in the normal app list, likely due to security reasons.

1. In your **VR Headset**, navigate to your App Library (waffle button).
2. Look for a filter or search option, which usually looks like 3 horizontal lines or a key.
3. In the options, filter by apps with **Unknown Sources**. This should reveal all custom apps, which you can now select from.

## App Overview

An overview of each custom app. Each is in a different stage of development. We'll use a scale to distinguish this concisely.

| Stage # | Stage Name  | Focus                                                      |
| :-----: | ----------- | ---------------------------------------------------------- |
|    1    | Planning    | Discussion of major app features and outline.              |
|    2    | Setup       | App environment is being set up.                           |
|    3    | Development | Main app development. Features might be adjusted slightly. |
|    4    | Polishing   | Bug fixes and quality-of-life improvements.                |
|    5    | Launch      | App is ready for deployment.                               |

### Board Games

An interactive multiplayer over-the-board social experience. Play **Cards**, **Checkers** or **Chess** online with friends or family. Or, play **Connect 4** against a bot.

As of May 2025, the **Board Games** app is in **Stage 4: Polishing**.

### Park

A peaceful recreational retreat to a local park, complete with a motorboat and electric scooter. Designed with multiplayer outdoor experiences in mind. (needs testing) More activities coming soon!

As of May 2025, the **Park** app is in **Stage 3: Development**.

### Arcade

An action-packed competitive paridise, borrowing elements from carnivals and traditional arcades. Play multiplayer 1v1 hoops, knock down bottles with a water gun, or earn the highest score in skee-ball.

As of May 2025, the **Arcade** app is in **Stage 2: Setup**.

## Packages

This is not an exhaustive list, as not all packages show in the package manager.

#### Features

-   Engineering (`unity.feature.engineering`)
    -   Various tools for development environment
-   VR (`unity.feature.vr`)
    -   Various tools for VR development

#### Packages

-   Unity Input System
    -   New-ish input control that allows for better input configuration.
-   Oculus XR Plugin
    -   Support for Oculus devices
-   Photon PUN
    -   Provides networking support. `Window -> Photon Unity Networking -> PUN Wizard`
    -   `PhotonServerSettings` should contain several IDs, linking the project to a specific account with PUN servers.
-   ProBuilder
    -   Tool for building more advanced custom shapes
-   TextMeshPro
    -   Tool for non-UI based text elements
-   Universal RP
    -   Optimized pipeline for rendering. Might cause issues with imported materials. To convert standard materials to URP-enabled ones, select all materials and navigate to `Edit -> Rendering -> Materials -> Convert Selected Built-in Materials to URP`
-   XR Interaction Toolkit
    -   System for building XR interactions and objects

#### Asset Store

-   [Voxel office props](https://assetstore.unity.com/packages/3d/props/voxel-office-props-127772)
    -   Laptop, desktop monitor, glass table
-   [Rocks and Boulders 2](https://assetstore.unity.com/packages/3d/props/exterior/rock-and-boulders-2-6947)
    -   Rocks in exterior environment
-   [BPS Apartment Kit](https://assetstore.unity.com/packages/3d/environments/apartment-kit-124055)
    -   Prebuilt modular apartment assets
-   [Playing Cards Pack](https://assetstore.unity.com/packages/3d/props/tools/free-playing-cards-pack-154780)
    -   Playing cards models
-   [Exploding Bottles](https://assetstore.unity.com/packages/3d/props/guns/exploding-bottles-255996)
    -   Breakable bottles for arcade water gun game
-   [Legacy Particle pack](https://assetstore.unity.com/packages/vfx/particles/legacy-particle-pack-73777)
    -   Sample particles modified to create water gun effect
-   [Plasma Guns](https://assetstore.unity.com/packages/3d/props/guns/plasma-guns-set-lite-smg-179430)
    -   Plasma gun adapted as a water gun for arcade
-   [Electric scooter](https://assetstore.unity.com/packages/3d/props/exterior/electric-scooter-prop-171335)
    -   Electric scooter available in park

#### Other sources

-   [Standing Desk](https://sketchfab.com/3d-models/standing-desk-65a7f4b06a5f4954a0d43eb8812dd165)
    -   Adjustable table used in all game scenes
-   Chess set
-   Checkers set
-   [Connect 4 set](https://sketchfab.com/3d-models/connect-4-90bc2c11ed694147be30413c3ac05de7)
    -   Connect 4 pieces and board

## Asset Reference

A deeper dive into specific assets within each custom app.

-   [D] = deprecated

### Board Games

#### Scenes

-   **Mainmenu**
    -   Entrypoint room with a game selector. Set up for cards and checkers, with other games located on the back of the selector.
-   **ChessScene** & **CheckersScene**
    -   Standard game scenes with a board and pieces. Multiplayer only. Can be reset or left with specific buttons.
-   **Connect4Scene**
    -   Similar to standard game scenes, but not built for multiplayer. A laptop displays the current turn and a custom bot plays after each human move.
-   **CardsScene**
    -   Similar to other games, but with a more complex game manager. New card game presets can be created using a custom scriptable object. These options are selectable by a dial on the side table.

#### Prefabs

| Name                         | Scenes                        | Usage                                                                                         |
| ---------------------------- | ----------------------------- | --------------------------------------------------------------------------------------------- |
| **C4ChipR/Y**                | **Connect4**                  | Interactable connect 4 pieces.                                                                |
| **C4ChipR/YDummy**           | **Connect4**                  | Uninteractable connect 4 pieces used in board animations.                                     |
| **Checkers**                 | **Checkers**                  | Fully interactive checkers set.                                                               |
| **Chess**                    | **Chess**                     | Fully interactive chess set.                                                                  |
| **complete scoretracker**    | **Checkers, Chess, Connect4** | Fully interactive disk scoretracker.                                                          |
| **controldesk**              | **Cards, Checkers, Connect4** | Side desk for setting card game (this is disabled in non-cards scenes) or returning to lobby. |
| **Counter**                  | **Checkers, Chess, Connect4** | Single disk used in scoretracker.                                                             |
| **ExitButton** [D]           | **None**                      | Sign and button for returning to main menu.                                                   |
| **Foliage**                  | **All**                       | Natural environment outside windows.                                                          |
| **GamePieceRecoverySystem**  | **All**                       | Recovers game pieces that fall off the table.                                                 |
| **Jenga** [D]                | **None**                      | Fully interactive jenga set. Replaced with cards.                                             |
| **Jenga Piece** [D]          | **None**                      | Single jenga piece.                                                                           |
| **Left/Right Hand Presence** | **All**                       | Internal component for XR rig.                                                                |
| **LevelSelectorWidget** [D]  | **None**                      | Old UI-based game selector.                                                                   |
| **modified_button** [D]      | **Some**                      | V1 poke button, based on XRI toolkit.                                                         |
| **modified_buttonV2** [D]    | **Some**                      | V2 poke button, cleaner press with highlight animation.                                       |
| **NetworkStatusIndicator**   | **All**                       | Indicator for Wifi connection.                                                                |
| **PhotonUtilities**          | **All**                       | Component containing all necessary controllers for networking and voice.                      |
| **Push Button**              | **None**                      | Basic unmodified button from XRI toolkit.                                                     |
| **RoomV2**                   | **All**                       | House-like environment used in all scenes.                                                    |
| **Scoretracker**             | **Some**                      | Frame for scoretracker, no counters.                                                          |
| **StandDesk_pre**            | **All**                       | Adjustable desk.                                                                              |
| **VideoPlayer** [D]          | **None**                      | Video player for tutorials, removed.                                                          |
| **XR Rig**                   | **All**                       | Player XR rig.                                                                                |

#### Scripts

| Name                           | Description                                                                                                                                                      |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AdjustableDesk                 | Controls adjustable desk. Operates in steps, so pressing up or down moves the desk a set amount.                                                                 |
| AdjustableDeskCollider         | The top of the desk has a large collider that sets any grabbable object to be a child of the desk. This avoids the problem of objects falling through the table. |
| AppConstants [D]               | Intended for global tracking of room key, not used at the moment.                                                                                                |
| CardGameConfig                 | Scriptable object for defining card games.                                                                                                                       |
| CardHolder                     | Snap-based card holder config.                                                                                                                                   |
| CardManager                    | Controls active card game and tracks cards and holders.                                                                                                          |
| CardSoundEffect                | Card sound effect on collision. There is probably a better way to do this within the XR grab interactable script.                                                |
| CardStacking                   | Allows card to be stackable in a deckpoint.                                                                                                                      |
| Connect4                       | Controls active Connect 4 instance.                                                                                                                              |
| Connect4BotStandard            | Standard difficulty bot (non-AI) for C4.                                                                                                                         |
| Connect4Piece                  | Controls connect 4 piece, allowing plays.                                                                                                                        |
| Connect4Utils                  | Houses common functionality for Connect 4 and bot. (win detection)                                                                                               |
| ContinuousMovement             | Enables joystick player movement.                                                                                                                                |
| Deckpoint                      | Snap-bsed card stacker config and management.                                                                                                                    |
| DisplayObjectAnimation         | Animates choices above game selector panel.                                                                                                                      |
| ExitButton                     | Allows exit button to return player to lobby.                                                                                                                    |
| GamePieceRecoverySystem        | Automatically recovers fallen game pieces to the table.                                                                                                          |
| GameSelector                   | Allows selection of board games in main menu.                                                                                                                    |
| Highlight                      | Enables highlighting of selected or hovered game pieces.                                                                                                         |
| IConnect4Bot                   | Generic interface for connect 4 bots, enabling hot swapability in the future.                                                                                    |
| ITabletopManager               | Generic interface for multiple different game managers, interfaces with GPRS.                                                                                    |
| LineDrawer                     | Draws winning sequence for Connect 4.                                                                                                                            |
| NetworkInstantiateCallback     | Used to set parent of instanted GameObjects across network. Only used in the cards game, as parent/child relationships are not synced by default.                |
| NetworkManager                 | Controls Photon Network.                                                                                                                                         |
| NetworkPlayerScript            | Controls player in network context.                                                                                                                              |
| NetworkPlayerSpawner           | Spawns network player upon joining Photon room.                                                                                                                  |
| NetworkStatusIndicator         | Checks for internet connection to provide a visual indicator.                                                                                                    |
| OffsetInteractable [D]         | Unimplemented copy of XRGrabInteractable, but not sure if this is used.                                                                                          |
| OptionsMenu [D]                | Script controling old UI-based options menus.                                                                                                                    |
| PlayerController               | Player movement. Unclear exactly how much of this is necessary.                                                                                                  |
| RestartScene [D]               | Restarts current scene. Not a very good user experience, so avoid using.                                                                                         |
| RotateObject [D]               | Rotates an object, not clear if this is used. Probably should be integrated into another script if so.                                                           |
| SampleAvatarEntityCustom       | Used to create custom sample avatars from Meta avatars. Not implemented anywhere but might be useful later.                                                      |
| ScoretrackerCounterRestrict    | Supposed to constrict movement of scoretracker disks. Actually just slows their velocity down.                                                                   |
| SelectUI [D]                   | Part of the old ray selector. Not used after removal of old UI-based selectors.                                                                                  |
| TabletopManager                | Generic game piece manager. Supports GPRS and resetting game pieces. Does not support instantiation of pieces at runtime.                                        |
| TeleportScript                 | Not used in Board Games anymore. Enables ray-teleporting.                                                                                                        |
| VideoPlayerScript [D]          | Enables video players. No longer used after tutorial video removal.                                                                                              |
| XRGrabNetworkInteractable      | Enables an object to be grabbable in VR and tracked through the network. Make sure these objects also have a photon view and rigidbody.                          |
| XRGrabNetworkInteractableCards | Same as previous, but unclear if this is actually used.                                                                                                          |
| XRPlayerController             | Controls XR player. Same issue as PlayerController, these scripts might need to be merged/consolidated.                                                          |

### Park

Note: The original version of Park is a copy of the Board Games app. Thus, there is significant overlap in objects/scripts. Many of the assets in this project are not used and could be cleaned up.

#### Scenes

-   **ParkScene**
    -   Entrypoint room with all activities. Enter the blue circle on the dock to enter the boat or the larger circle in the water to exit. Approach the scooter to mount.
-   **ScooterScene**
    -   A testing scene for scooter control and configuration not included in the build.

#### Prefabs

| Name                         | Scenes        | Usage                                                                                      |
| ---------------------------- | ------------- | ------------------------------------------------------------------------------------------ |
| **Boat/variants**            | **ParkScene** | Rideable boat that floats on water.                                                        |
| **Left/Right Hand Presence** | **All**       | Internal component for XR rig.                                                             |
| **LevelSelectorWidget** [D]  | **None**      | Old UI-based game selector.                                                                |
| **Paddle** [D]               | **ParkScene** | Grabbable paddle for rowboat. Removed due to difficulties with snapping/pivoting properly. |
| **PhotonUtilities**          | **All**       | Component containing all necessary controllers for networking and voice.                   |
| **Scooter**                  | **Some**      | Rideable electric scooter. Multiple color variants exist.                                  |
| **VideoPlayer** [D]          | **None**      | Video player for tutorials, removed.                                                       |
| **Waterfall**                | **ParkScene** | Waterfall particle effect found in main scene.                                             |
| **XR Rig**                   | **All**       | Player XR rig.                                                                             |

#### Scripts

| Name                      | Description                                                                                                                             |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| AppConstants [D]          | Intended for global tracking of room key, not used at the moment.                                                                       |
| BoatController            | Controls boat movement and floating.                                                                                                    |
| BoatDismounter            | Allows for boat dismount points, which enable the player to exit the boat when entered.                                                 |
| BoatMounter               | Allows for boat mount points, which enable the player to enter the boat when entered.                                                   |
| ContinuousMovement        | Enables joystick player movement.                                                                                                       |
| JetSkiScript [D]          | Controls jet ski movement, which are no longer part of the scene.                                                                       |
| LeaveDock                 | Part of the mount/dismount point system. Controls which collider is enabled, preventing multiple players from mounting the boat.        |
| LeaveMountArea            | Part of the mount/dismount point system. Controls which collider is enabled, preventing multiple players from dismounting the boat.     |
| MountScooter              | Enables proximity mounting of scooter.                                                                                                  |
| NetworkManager            | Controls Photon Network.                                                                                                                |
| NetworkPlayerScript       | Controls player in network context.                                                                                                     |
| NetworkPlayerSpawner      | Spawns network player upon joining Photon room.                                                                                         |
| Paddle [D]                | Controls motion and snap-back of rowboat paddle. Not working properly.                                                                  |
| PlayerController          | Player movement. Unclear exactly how much of this is necessary.                                                                         |
| Scooter                   | Controls scooter movement and steering joint.                                                                                           |
| SelectUI [D]              | Part of the old ray selector. Not used after removal of old UI-based selectors.                                                         |
| TeleportScript            | Enables ray-teleporting.                                                                                                                |
| VideoPlayerScript [D]     | Enables video players. No longer used after tutorial video removal.                                                                     |
| WaterManager              | Controls water mesh visual.                                                                                                             |
| WaveManager               | Callback for wave height used by the boat. Could possibly be merged with WaterManager in the future.                                    |
| XRGrabNetworkInteractable | Enables an object to be grabbable in VR and tracked through the network. Make sure these objects also have a photon view and rigidbody. |
| XRPlayerController        | Controls XR player. Same issue as PlayerController, these scripts might need to be merged/consolidated.                                 |

### Arcade

#### Scenes

-   **Demo**
    -   Entrypoint room with starter arcade environment. Arcade and carnival games will be here when those are finished.
-   **watergun_temp**
    -   Experimental scene for water gun particles and knocking over glass bottles. Not in build.
-   **SkeeBallScene**
    -   Experimental scene for skee ball game. Not in build.

#### Prefabs

| Name                         | Scenes   | Usage                                                                    |
| ---------------------------- | -------- | ------------------------------------------------------------------------ |
| **Left/Right Hand Presence** | **All**  | Internal component for XR rig.                                           |
| **LevelSelectorWidget** [D]  | **None** | Old UI-based game selector.                                              |
| **PhotonUtilities**          | **All**  | Component containing all necessary controllers for networking and voice. |
| **VideoPlayer** [D]          | **None** | Video player for tutorials, removed.                                     |
| **XR Rig**                   | **All**  | Player XR rig.                                                           |

#### Scripts

| Name                      | Description                                                                                                                             |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| AppConstants [D]          | Intended for global tracking of room key, not used at the moment.                                                                       |
| BumpScript                | Experimental script for adding velocity to skee ball throws. Should probably be combined with SkeeBallScript                            |
| ContinuousMovement        | Enables joystick player movement.                                                                                                       |
| NetworkManager            | Controls Photon Network.                                                                                                                |
| NetworkPlayerScript       | Controls player in network context.                                                                                                     |
| NetworkPlayerSpawner      | Spawns network player upon joining Photon room.                                                                                         |
| PlayerController          | Player movement. Unclear exactly how much of this is necessary.                                                                         |
| SelectUI [D]              | Part of the old ray selector. Not used after removal of old UI-based selectors.                                                         |
| SkeeBallScript            | Controls skee ball motion. Incomplete.                                                                                                  |
| TeleportScript            | Enables ray-teleporting.                                                                                                                |
| VideoPlayerScript [D]     | Enables video players. No longer used after tutorial video removal.                                                                     |
| XRGrabNetworkInteractable | Enables an object to be grabbable in VR and tracked through the network. Make sure these objects also have a photon view and rigidbody. |
| XRPlayerController        | Controls XR player. Same issue as PlayerController, these scripts might need to be merged/consolidated.                                 |

## Future Directions

Some tasks on the roadmap.

### Bugs

-   **[BoardGames]** Game pieces recovered with `GamePieceRecoverySystem` are sometimes floating for certain players in a multiplayer session.
-   **[BoardGames]** Scene switching causes tearing in the headset, which could disorient users. Also, immense lag on joining Photon rooms, which might be able to be fixed by having a lobby room, which we connect to before switching rooms.
-   **[Park]** Scooter driving is unstable and could cause motion sickness
-   **[Park]** Land is missing collision in certain places, allowing the boat to pass through
-   **[Park]** Boat collisions with land are buggy and problematic
-   **[Park]** Missing teleport reticle and teleport zone is improperly set up, so most of the map is not teleportable

### Future features

-   **[All]** Audio/music control menu
-   **[All]** Use [Meta Avatars](https://www.meta.com/avatars/) in the projects. This has proved challenging to work, as avatars are generated according to a script at runtime. Nontrivial to get working with Photon PUN.
-   **[Park]** Add basketball
-   **[Park]** Adapt boat/scooter physics to a golf cart
-   **[Arcade]** Finalize environment
-   **[Arcade]** Add completed water gun + bottles game to environment

## Development Timeline

### Developers

| Name           | Github                                                              | Start date | End date |
| -------------- | ------------------------------------------------------------------- | ---------- | -------- |
| Jacob Stolker  | [erifyc1](https://github.com/erifyc1)                               | Aug 2022   | May 2025 |
| Sainath Ganesh | [FurySwordXD](https://github.com/FurySwordXD)                       | Aug 2023   | Dec 2023 |
| Ben Guan       | [mumbler6](https://github.com/mumbler6)                             | Aug 2023   | May 2024 |
| Emre Eraslan   | [vo-dh](https://github.com/vo-dh)                                   | Aug 2023   | Present  |
| Sai Hariharan  | [SaiMeenakshi-Hariharan](https://github.com/SaiMeenakshi-Hariharan) | Aug 2024   | Present  |

### Key Design Decisions

1. 2-dimensional user interface is not immersive
    - We originally had several 2D menus with a ray selector to pick options. These proved difficult to use and broke immersiveness of the apps.
    - We've since moved on to physical buttons that can be pressed to perform certain actions. See XR interaction toolkit sample project [here](https://www.youtube.com/watch?v=dCVAYB2jkEY) for some great examples. These are already imported in some projects.
    - We reserve 2D UI for non-interactive displays. This seems to work, especially if on a virtual tv or computer screen. Avoid moving these menus or making them follow the player.
2. Avoid ultra-realistic assets or geometry
    - We've had some extremely detailed assets before, but these fail to contribute to the projects enough to be worth the cost for several reasons:
        - High resolution textures and models can be over the Github file size limit, making it difficult to track these files.
        - These assets can be difficult for the VR headsets to handle. Huge assets blow up the build size and dramatically cut the framerate, reducing the quality of the user experience.
        - It's nearly impossible to maintain ultra-realism across all objects in the game. Having a mix of a few high quality and medium/lower quality assets can make the experience less uniform.
3. Minimize input complexity as much as possible
    - During our studies and testing sessions, we found that participants tended to button mash, despite any amount of prior training on controls.
    - We used to have many additional controls bound to buttons on the controller, including ray-select, opening menus, returning to lobby, and teleporting. Often, participants would bump into these, causing what seemed like random teleports and other confusing actions. Though it might seem counter-intuitive to have most controller buttons do nothing, this provides the safest experience for new users.
    - All of these have been removed and some were replaced with 3D button panels in the scene. It might also be worth mirroring all controls to both hands, as users tend to not pay close attention to which controls are on a specific hand/side. For example, joystick movement is only available on the left hand.
4. Velocity tracking for XR grab objects
    - XR grab object have three modes for tracking _velocity tracking_, _instantaneous_, and _kinematic_. More information is available [**here**](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.0/manual/xr-grab-interactable.html).
        - Velocity tracking adjusts the velocity of the object towards your hand.
        - Instantaneous instantly adjusts the position to the object to your hand's position.
        - Kinematic eases the object's position towards your hand, but requires the rigidbody to be kinematic, meaning gravity and other-object collisions are not respected.
    - Velocity tracking is the least accurate

### History

#### Fall 2022

-   preliminary research into VR app preferences
-   Equipment and app purchases
-   VR headset and PC setup
    ![lab setup](https://i.imgur.com/NGdRJcm.jpeg)

#### Spring 2023

-   Preliminary setup and testing
-   barebones gabbable objects ([demo](https://www.youtube.com/watch?v=VuEmuVKoQfA))
-   basic networking/multiplayer ([demo](https://www.youtube.com/watch?v=xRUicDUixMg))

#### Fall 2023

-   lobby and game selector ([demo](https://www.youtube.com/watch?v=xvRinayI1II))
    ![nov23 game select setup](https://i.imgur.com/u2AaMN2.png)
-   disk score tracker
    ![nov23 score tracker](https://i.imgur.com/VQl7TMv.png)
-   work towards in-game tutorial ([demo](https://www.youtube.com/watch?v=tU6PpK7Ytug))
-   initial work on park environment
    ![nov23 park1](https://i.imgur.com/bwvrppF.jpeg)
    ![nov23 park2](https://i.imgur.com/8RysApt.jpeg)
    ![nov23 park3](https://i.imgur.com/8RaeVtv.jpeg)

#### Spring 2024

-   park rowboat paddles ([demo](https://www.youtube.com/watch?v=KGy23-pkG9U))
    ![jan24 paddles](https://i.imgur.com/l5NbECR.png)
-   park scooter
    ![jan24 scooter env](https://i.imgur.com/zREGpNq.png)
-   score tracker adjustment and ui menus ([demo](https://www.youtube.com/watch?v=cE6rEG0DcJw))
-   started on arcade app
    ![jan24 arcade starter](https://i.imgur.com/oIq9QsO.png)
-   replace jenga game with playing cards
-   add poke interactors to fingers, paving the way for non-UI selectors
-   added adjustable standing desk

#### Fall 2024

-   card game adjustments
-   quality of life changes
-   new dev onboarding

#### Spring 2025

-   environment revamp to homey theme
    ![new theme](https://i.imgur.com/zi1SmA9.png)
-   new game selector and flat-UI removal ([demo](https://www.youtube.com/watch?v=XriDaKRMgLI))
-   cards rework and debugging
    ![card holder original](https://i.imgur.com/0sxzKiw.png)
    ![card holder new](https://i.imgur.com/J8ve9LO.png)
    ![side table selector](https://i.imgur.com/it1vxA3.png)
    ![fixed deckpoints](https://i.imgur.com/00vnPwX.png)
-   park scooter and boat upgrades ([demo](https://www.youtube.com/watch?v=-gRF12_rl3w))
    ![scooter collision changes](https://i.imgur.com/kHv6ygb.png)
-   connect 4 game ([demo](https://www.youtube.com/watch?v=oLKtZW_aLss))
