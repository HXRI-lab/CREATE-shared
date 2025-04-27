# Setup

## Environment Setup

1. Install [Unity Hub](https://unity.com/unity-hub) and current editor version (2022.3.10f1)
2. Install [Visual Studio](https://visualstudio.microsoft.com/vs/unity-tools/) and make sure to add C#/Unity dev tools
3. Clone the repository
   `git clone <project_name.git>`
4. In Unity Hub, choose `Add -> Add project from disk`
5. Make sure the Unity Editor version is correct before launching

## Headset Setup

1. If headset is new, follow Meta's setup guidelines
2. Once paired and connected to a phone, enable **Developer Mode** in the headset's settings.
    - If this option is not available, your account may need additional steps to be allowed to use developer mode. This might include accepting terms, adding a payment method, confirming a phone number, etc.

## Building the App

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

## Running the App

Note: These steps are likely to change due to constant UI updates. Custom apps do not show up in the normal app list, likely due to security reasons.

1. In your **VR Headset**, navigate to your App Library (waffle button).
2. Look for a filter or search option, which usually looks like 3 horizontal lines or a key.
3. In the options, filter by apps with **Unknown Sources**. This should reveal all custom apps, which you can now select from.
