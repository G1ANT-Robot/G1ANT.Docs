# UI Recorder

The UI Recorder addon is a special tool designed to create embedded scripts based on recorded user actions. You could compare it to macro recording functions in such applications as MS Office or Adobe Photoshop.

## How to Use

1. In order to use this addon, you need to activate it first, just like you do with any other addons: in the Addons panel to the left of the G1ANT.Robot window click to select the box next to the `recorder` item, thus enabling the addon.

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/enable_recorder.png)

2. Now, select `UI Script` from `Insert` menu.

3. In the resulting *Select process to record* window select the application, in which you want your actions to be recorded. In this example WordPad was selected:

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/select_process.png)

4. The selected application should be brought to the foreground and a special recording panel should appear with the buttons to start and stop recording or exit the recorder.

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/recorder_panel.png)

5. To start recording your actions, just click Record button and perform actions in the selected application. Every successfully recorded action will be previewed in a summary window, which is displayed for 5 seconds above the recording buttons:

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/ui-summary.png)

   A red window background means an error in event handling by the recorder.

6. When you are done, click Stop button. If you don’t want to record more actions, click Exit button.

7. The `recorder.play` command along with the script name of recorded actions is automatically added to your code. You can also use the optional `delayratio` argument, which sets a replay delay between consecutive actions as a factor of 250ms (the `delayratio` set to 4 means 1s delay).

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/recorder_script.png)

When you run the robot script, all recorded events will be executed. Any errors which might occur during the execution of the UI script will not stop it. To stop the UI script, stop the process by pressing **Ctrl+F12**.

## Changes to the Recorded Script

It is possible to change some values recorded in the UI script:

1. Define a variable in the robot script, for example

   ```G1ANT
   ♥filename = document.doc
   ```

2. Select `UI Session Manager` from `View` menu. A new panel appears on the right of the script editor. Here, you can select a script with recorded actions, view its content, set variables and import/export UI scripts from/to a file.

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/ui-script-panel.png)

3. Select the desired UI script from the *Embedded UI session* drop-down list.

4. For the *Value* events you can set variables declared in the robot script: just right-click a *Value* item and select *Set variable…* from the context menu or click `V` button on the panel’s toolbar.

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/ui-set-value.png)

5. In the resulting *Variable* dialog box enter the name of a variable you want to use in the UI script. In this case, it would be the `♥filename` variable declared before:

   ![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/ui-variable.png)

When you run your robot script, the value stored in the  `♥filename` variable will be passed to the UI script, so the element *document.doc* will be clicked in WordPad.

## Saving UI Scripts

In order to preserve UI scripts in robot scripts, it’s required to save your scripts in binary format, which is the default setting when at least one UI script is present. What’s more important, when you enter a name for the binary file, you will be provided with an option of password-protecting the file:

![](https://github.com/G1ANT-Robot/G1ANT.Manual/raw/develop/-assets/file-password.png)