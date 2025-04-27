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
