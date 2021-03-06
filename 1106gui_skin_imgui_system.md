# GUI Skin (IMGUI System)

GUISkins are a collection of GUIStyles that can be applied to your GUI. Each Control type has its own Style definition. Skins are intended to allow you to apply style to an entire UI, instead of a single Control by itself.

GUISkins 是一组可以应用到 GUI 的 GUIStyles 。每个控件 (Control) 类型都有各自的样式 (Style) 定义。皮肤使您能够将一种样式应用于整个 UI，而不只是应用于单个控件 (Control)。

![A GUI Skin as seen in the Inspector](Main/Inspector-GUISkin.png)
######A GUI Skin as seen in the Inspector
To create a GUISkin, select Assets->Create->GUI Skin from the menubar.

如需创建 GUISkin，请在菜单栏上选择资源 (Assets) -> 创建 (Create) -> GUI 皮肤 (GUI Skin) 。

**Please Note: **This page refers to part of the IMGUI system, which is a scripting-only UI system. Unity has a full GameObject-based UI system which you may prefer to use. It allows you to design and edit user interface elements as visible objects in the scene view. See the UI System Manual for more information.

GUISkin 是 UnityGUI 系统的一部分。有关 UnityGUI 的更多详细信息，请参阅 GUI 脚本指南.

##Properties

All of the properties within a GUI Skin are an individual GUIStyle. Please read the GUIStyle page for more information about how to use Styles.

GUI 皮肤中的所有属性都是一个独立的 GUIStyle 。有关如何使用样式 (Style) 的更多信息，请参阅GUIStyle 页。

| Property:	 | Function: |
| -- | -- |
| **Font**	 | The global Font to use for every Control in the GUI |
| **Box**	 | The Style to use for all Boxes |
| **Button**	 | The Style to use for all Buttons |
| **Toggle**	 | The Style to use for all Toggles |
| **Label**	 | The Style to use for all Labels |
| **Text Field**	 | The Style to use for all Text Fields |
| **Text Area**	 | The Style to use for all Text Areas |
| **Window**	 | The Style to use for all Windows |
| **Horizontal Slider**	 | The Style to use for all Horizontal Slider bars |
| **Horizontal Slider Thumb**	 | The Style to use for all Horizontal Slider Thumb Buttons |
| **Vertical Slider**	 | The Style to use for all Vertical Slider bars |
| **Vertical Slider Thumb**	 | The Style to use for all Vertical Slider Thumb Buttons |
| **Horizontal Scrollbar**	 | The Style to use for all Horizontal Scrollbars |
| **Horizontal Scrollbar Thumb**	 | The Style to use for all Horizontal Scrollbar Thumb Buttons |
| **Horizontal Scrollbar Left Button	** | The Style to use for all Horizontal Scrollbar scroll Left Buttons |
| **Horizontal Scrollbar Right Button**	 | The Style to use for all Horizontal Scrollbar scroll Right Buttons |
| **Vertical Scrollbar**	 | The Style to use for all Vertical Scrollbars |
| **Vertical Scrollbar Thumb**	 | The Style to use for all Vertical Scrollbar Thumb Buttons |
| **Vertical Scrollbar Up Button**	 | The Style to use for all Vertical Scrollbar scroll Up Buttons |
| **Vertical Scrollbar Down Button**	 | The Style to use for all Vertical Scrollbar scroll Down Buttons |
| **Custom 1–20**	 | Additional custom Styles that can be applied to any Control |
| **Custom Styles**	 | An array of additional custom Styles that can be applied to any Control |
| **Settings**	 | Additional Settings for the entire GUI |
|         Double Click  | Selects Word	If enabled, double-clicking a word will select it |
|         Triple Click  | Selects Line	If enabled, triple-clicking a word will select the entire line |
|         Cursor Color	 | Color of the keyboard cursor |
|         Cursor Flash  | Speed	The speed at which the text cursor will flash when editing any Text Control |
|         Selection Color	 | Color of the selected area of Text |
##Details

When you are creating an entire GUI for your game, you will likely need to do a lot of customization for every different Control type. In many different game genres, like real-time strategy or role-playing, there is a need for practically every single Control type.

为游戏创建整个 GUI 时，您可能需要为各种不同类型的控件 (Control) 做大量自定义。在许多不同的游戏类型中（如即时战略游戏或角色扮演游戏），几乎每种控件 (Control) 类型都需要自定义。

Because each individual Control uses a particular Style, it does not make sense to create a dozen-plus individual Styles and assign them all manually. GUI Skins take care of this problem for you. By creating a GUI Skin, you have a pre-defined collection of Styles for every individual Control. You then apply the Skin with a single line of code, which eliminates the need to manually specify the Style of each individual Control.

由于每个独立的控件 (Control) 都使用特殊的样式 (Style)，因此不必创建十几个不同的样式并手动指定。GUI 皮肤 (GUI Skins) 将为您解决这个问题。通过创建 GUI 皮肤 (GUI Skin)，您可以获得一组预先定义的针对每个独立控件 (Control) 的样式 (Styles)。之后，应用带有一行代码的皮肤 (Skin)，这样您就不必手动为每个独立的控件 (Control) 指定样式 (Style) 了。

###Creating GUISkins

GUISkins are asset files. To create a GUI Skin, select Assets->Create->GUI Skin from the menubar. This will put a new GUISkin in your Project View.

GUISkin 是资源文件。如需创建 GUI 皮肤 (GUI Skin)，请从菜单栏选择资源 (Assets) -> 创建 (Create) -> GUI 皮肤 (GUI Skin) 。您的工程视图 (Project View中会出现新的 GUISkin。

![A new GUISkin file in the Project View](Main/GUISkin-ProjectView.png)
######A new GUISkin file in the Project View
###Editing GUISkins

After you have created a GUISkin, you can edit all of the Styles it contains in the Inspector. For example, the Text Field Style will be applied to all Text Field Controls.

创建 GUISkin 后，您可以编辑检视器 (Inspector) 中包含的所有样式 。例如，文本框 (Text Field) 样式将会应用于所有文本框控件 (Text Field Controls)。

![Editing the Text Field Style in a GUISkin](Main/GUISkin-EditingTextField.png)
######Editing the Text Field Style in a GUISkin
No matter how many Text Fields you create in your script, they will all use this Style. Of course, you have control over changing the styles of one Text Field over the other if you wish. We’ll discuss how that is done next.

无论脚本中创建了多少个文本框 (Text Field)，它们都将使用此样式。当然，如果您愿意，您可以更改某个文本框 (Text Field) 的样式。接下来我们将讨论如何进行以上操作。that is done next.

###Applying GUISkins

To apply a GUISkin to your GUI, you must use a simple script to read and apply the Skin to your Controls.

要将 GUISkin 应用到 GUI，您必须用简单的脚本来读取皮肤 (Skin) 并将其应用于控件 (Control)。

```
    // Create a public variable where we can assign the GUISkin
    var customSkin : GUISkin;

    // Apply the Skin in our OnGUI() function
    function OnGUI () {
        GUI.skin = customSkin;

        // Now create any Controls you like, and they will be displayed with the custom Skin
        GUILayout.Button ("I am a re-Skinned Button");

        // You can change or remove the skin for some Controls but not others
        GUI.skin = null;

        // Any Controls created here will use the default Skin and not the custom Skin
        GUILayout.Button ("This Button uses the default UnityGUI Skin");
    }
```

In some cases you want to have two of the same Control with different Styles. For this, it does not make sense to create a new Skin and re-assign it. Instead, you use one of the Custom Styles in the skin. Provide a Name for the custom Style, and you can use that name as the last argument of the individual Control.

某些情况下，您需要两个拥有不同样式 (Style) 的同一控件 (Control)。这时，没必要创建一个新皮肤 (Skin) 并进行重新指定。相反，您可以使用皮肤中的某个自定义 (Custom) 样式 (Style)。为自定义样式 (Style) 取一个名字 (Name) ，这样您便能够将这个名字作为该独立控件 (Control) 的最后一个参数加以使用。
```
    // One of the custom Styles in this Skin has the name "MyCustomControl"
    var customSkin : GUISkin;

    function OnGUI () {
        GUI.skin = customSkin;

        // We provide the name of the Style we want to use as the last argument of the Control function
        GUILayout.Button ("I am a custom styled Button", "MyCustomControl");

        // We can also ignore the Custom Style, and use the Skin's default Button Style
        GUILayout.Button ("I am the Skin's Button Style");
    }
```
For more information about working with GUIStyles, please read the GUIStyle page. For more information about using UnityGUI, please read the GUI Scripting Guide.

有关使用 GUIStyle 的更多信息，请参阅 GUIStyle 页面。有关使用 UnityGUI 的更多信息，请参阅 GUI Scripting Guide 。