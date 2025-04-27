# Key Design Decisions

We've made quite a few pivots based on what we learned. It's best to keep a list, so we don't make the same mistakes over again.

## Design Decisions

1. **Avoid ultra-realistic assets or geometry**
    - We've had some extremely detailed assets before, but these fail to contribute to the projects enough to be worth the cost for several reasons:
        - High resolution textures and models can be over the Github file size limit, making it difficult to track these files.
        - These assets can be difficult for the VR headsets to handle. Huge assets blow up the build size and dramatically cut the framerate, reducing the quality of the user experience.
        - It's nearly impossible to maintain ultra-realism across all objects in the game. Having a mix of a few high quality and medium/lower quality assets can make the experience less uniform.
2. **Minimize input complexity as much as possible**
    - During our studies and testing sessions, we found that participants tended to button mash, despite any amount of prior training on controls.
    - We used to have many additional controls bound to buttons on the controller, including ray-select, opening menus, returning to lobby, and teleporting. Often, participants would bump into these, causing what seemed like random teleports and other confusing actions. Though it might seem counter-intuitive to have most controller buttons do nothing, this provides the safest experience for new users.
    - All of these have been removed and some were replaced with 3D button panels in the scene. It might also be worth mirroring all controls to both hands, as users tend to not pay close attention to which controls are on a specific hand/side. For example, joystick movement is only available on the left hand.
3. **Velocity tracking for XR grab objects**
    - XR grab object have three modes for tracking _velocity tracking_, _instantaneous_, and _kinematic_. More information is available [**here**](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@2.0/manual/xr-grab-interactable.html).
        - Velocity tracking adjusts the velocity of the object towards your hand.
        - Instantaneous instantly adjusts the position to the object to your hand's position.
        - Kinematic eases the object's position towards your hand, but requires the rigidbody to be kinematic, meaning gravity and other-object collisions are not respected.
    - Velocity tracking is the least accurate
4. **Use haptic and audio feedback whenever possible**
    - Feedback on virtual objects can greatly enhance immersiveness. We could definitely improve in this, so it's important to consider this in future development.
    - Examples of what we've implemented:
        - vibration on object pickup
        - noises when smacking certain objects together
        - sounds when pressing buttons
        - ambient music
        - object active noise (boat engine)
        - positive / negative sounds (valid or invalid moves in connect 4 have different sounds)
    - Future possibilities:
        - teleport or movement sounds
            - bonus: could also be ground-material dependent
        - sound or haptic when bumping into walls or objects
        - alter ambient music according to experience
        - object falling sound (whoosh)
        - different grab vibration variants for specific items
        - positive / negative vibrations
5. **Experiences should be designed with playing seated in mind**
    - Since we're aiming to build these apps for older adults, who may be limited in mobility and balance, it is best to ensure all activities can be played seated.
    - Many aspects of our games either function nicely for both sitting and standing or can switch between the two.
        - Ex. Adjustable standing desk

## Lessons Learned

1. **2-dimensional user interface is not immersive**
    - We originally had several 2D menus with a ray selector to pick options. These proved difficult to use and broke immersiveness of the apps.
    - We've since moved on to physical buttons that can be pressed to perform certain actions. See XR interaction toolkit sample project [here](https://www.youtube.com/watch?v=dCVAYB2jkEY) for some great examples. These are already imported in some projects.
    - We reserve 2D UI for non-interactive displays. This seems to work, especially if on a virtual tv or computer screen. Avoid moving these menus or making them follow the player.
2. **Advanced graphical effects and post-processing is not performant**
    - We've tried improving the quality of the environment by using various techniques:
        - real-time lighting & shadows
        - anti-aliasing
        - upscaled textures
        - reflective materials
    - While some of these improve the look of the scene slightly, many greatly reduce framerate. This tends to outweigh any benefit.
3. **Be extremely careful about VR motion sickness**
    - As developers with many hours in VR, it's easy to build up a tolerance to VR motion stickness.
    - If an addition causes a small amount of disorientation, it certainly needs to be tweaked to avoid problems with less experienced/tolerant users.
    - Be careful with:
        - Smooth joystick movement and rotation
        - Vehicles
        - Anything that teleports or moves the player
