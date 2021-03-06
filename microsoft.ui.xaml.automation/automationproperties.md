---
-api-id: T:Microsoft.UI.Xaml.Automation.AutomationProperties
-api-type: winrt class
---

<!-- Class syntax.
public class AutomationProperties : Windows.UI.Xaml.Automation.IAutomationProperties
-->

# Microsoft.UI.Xaml.Automation.AutomationProperties

## -description
Provides support for getting or setting instance-level values of automation properties. These property values are set as attached properties (typically in XAML) and supplement or override automation property values from a control's [AutomationPeer](../microsoft.ui.xaml.automation.peers/automationpeer.md).

## -remarks

### XAML attached properties

AutomationProperties is the host service class for several [XAML attached properties](/windows/uwp/xaml-platform/attached-properties-overview). The purpose of these attached properties is to enable setting various per-instance values that are pertinent to how a UI element is reported to the Microsoft UI Automation accessibility framework. This is useful in cases where the class design of the UI element doesn't already forward other UI-related property values as part of its Microsoft UI Automation integration or peer implementation behavior, or where the value being forwarded is not the value you want to report to Microsoft UI Automation.

In order to support XAML processor access to the attached properties, and also to expose equivalent get and set operations to code, each XAML attached property has a pair of **Get** and **Set** accessor methods, which are also members of AutomationProperties. For example, the [GetName](automationproperties_getname_1529049226.md) and [SetName](automationproperties_setname_400521346.md) methods support and provide the equivalent code-only support for reporting automation **Name** values to Microsoft UI Automation, instead of using the Name attached property to set it in XAML. Alternatively, you can use the dependency property system to get or set the value of the attached property, and this also reports the underlying value to Microsoft UI Automation. Call [GetValue](/uwp/api/windows.ui.xaml.dependencyobject.getvalue(windows.ui.xaml.dependencyproperty)) or [SetValue](/uwp/api/windows.ui.xaml.dependencyobject.setvalue(windows.ui.xaml.dependencyproperty,system.object)), passing the arguments of the dependency property identifier to set, and a reference to the target object on which to get or set the value.

#### Name property

Of the various attached properties, probably the most important one is **Name**. This is because it is the **Name** property that is most frequently accessed and reported by assistive technology when users interact with an app in an accessibility scenario. The **Name** serves as the human-readable identifier for the UI element.

Various UI elements have peer forwarding that can provide a default **Name** value based on other element properties. For example, the peer forwarding for the [Button](../microsoft.ui.xaml.controls/button.md) class will forward the **ToString** evaluation of the [Button](../microsoft.ui.xaml.controls/button.md) content and use this string as the default **Name**. In order to override that default, or to otherwise provide a **Name** value for any UI element case where there is no Microsoft UI Automation  **Name** available, set the **Name** attached property on that element in XAML. For more info on why a Microsoft UI Automation **Name** is important, see [Basic accessibility information](/windows/uwp/accessibility/basic-accessibility-information). For more info on how to test whether an element already has a peer-supplied **Name** that is useful, see [Accessibility testing](/windows/uwp/accessibility/accessibility-testing).

For localization reasons, you should avoid hard-coded string values for the **Name** in XAML. If you set [x:Uid directive](/windows/uwp/xaml-platform/x-uid-directive) on the element, then you can use RESW resources to target the property and provide different values for localization. For attached properties, the resource identifier form requires full qualification of the attached property in XAML form, including its namespace and a using: prefix. For example, to target the **AutomationProperties.Name** attached property value on a resource that has [x:Uid directive](/windows/uwp/xaml-platform/x-uid-directive) value of "sendButton", the **name** value of the **data** item in the RESW resources is `sendButton.[using:Windows.UI.Xaml.Automation]AutomationProperties.Name`

#### Attached properties

> [!NOTE]
> For more info about each attached property, see the page for the property's _Identifier field_.

| Attached property | Description |
| - | - |
| AcceleratorKey | Gets or sets the accelerator key for the specified element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.acceleratorkeyproperty">AcceleratorKeyProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getacceleratorkey">GetAcceleratorKey</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setacceleratorkey">SetAcceleratorKey</a></li></ul>|
| AccessibilityView | Gets or sets the Microsoft UI Automation tree view mode for an element.<ul><li>Type: [AccessibilityView](../microsoft.ui.xaml.automation.peers/accessibilityview.md)</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.accessibilityviewproperty">AccessibilityViewProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getaccessibilityview">GetAccessibilityView</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setaccessibilityview">SetAccessibilityView</a></li></ul>|
| AccessKey | Gets or sets the access key for the specified element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.accesskeyproperty">AccessKeyProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getaccesskey">GetAccessKey</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setaccesskey">SetAccessKey</a></li></ul>|
| AutomationId | Gets or sets the string that uniquely identifies the element to Microsoft UI Automation.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.automationidproperty">AutomationIdProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getautomationid">GetAutomationId</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setautomationid">SetAutomationId</a></li></ul>|
| Culture | Gets or sets the locale identifier for the automation element (for example, 0x0409 for "en-US" or English (United States)).<ul><li>Type: int</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.cultureproperty">CultureProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getculture">GetCulture</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setculture">SetCulture</a></li></ul>The value of the culture property for the specified element.|
| FullDescription | Gets or sets a localized string containing extended description text for an element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.fulldescriptionproperty">FullDescriptionProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getfulldescription">GetFullDescription</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setfulldescription">SetFullDescription</a></li></ul>|
| HeadingLevel | Gets or sets the heading level for a UI Automation element.<ul><li>Type: [AutomationHeadingLevel](../microsoft.ui.xaml.automation.peers/automationheadinglevel.md)</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.headinglevelproperty">HeadingLevelProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getheadinglevel">GetHeadingLevel</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setheadinglevel">SetHeadingLevel</a></li></ul>|
| HelpText | Gets or sets the help text for the element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.helptextproperty">HelpTextProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.gethelptext">GetHelpText</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.sethelptext">SetHelpText</a></li></ul>|
| IsDataValidForForm | Gets or sets a value that indicates whether the data is valid for the form.<ul><li>Type: Boolean</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.isdatavalidforformproperty">IsDataValidForFormProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getisdatavalidforform">GetIsDataValidForForm</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setisdatavalidforform">SetIsDataValidForForm</a></li></ul>|
| IsDialog | Gets or sets a value that indicates whether the automation element is a dialog window.<ul><li>Type: Boolean</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.isdialogproperty">IsDialogProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getisdialog">GetIsDialog</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setisdialog">SetIsDialog</a></li></ul>|
| IsPeripheral | Gets or sets a value that indicates whether the automation element represents peripheral UI.<ul><li>Type: Boolean</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.isperipheralproperty">IsPeripheralProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getisperipheral">GetIsPeripheral</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setisperipheral">SetIsPeripheral</a></li></ul>|
| IsRequiredForForm | Gets or sets a value that indicates whether the element is required to be filled out on a form.<ul><li>Type: Boolean</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.isrequiredforformproperty">IsRequiredForFormProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getisrequiredforform">GetIsRequiredForForm</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setisrequiredforform">SetIsRequiredForForm</a></li></ul>|
| ItemStatus | Gets or sets a description of the status of an item in an element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.itemstatusproperty">ItemStatusProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getitemstatus">GetItemStatus</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setitemstatus">SetItemStatus</a></li></ul>|
| ItemType | Gets or sets a description of the type of the specified element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.itemtypeproperty">ItemTypeProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getitemtype">GetItemType</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setitemtype">SetItemType</a></li></ul>|
| LabeledBy | Gets or sets the element that contains the text label for the element.<ul><li>Type: [UIElement](../microsoft.ui.xaml/uielement.md)</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.labeledbyproperty">LabeledByProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getlabeledby">GetLabeledBy</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setlabeledby">SetLabeledBy</a></li></ul>|
| LandmarkType | Gets or sets a [Landmark Type Identifier](/windows/desktop/WinAuto/landmark-type-identifiers) associated with an element.<ul><li>Type: [AutomationLandmarkType](../microsoft.ui.xaml.automation.peers/automationlandmarktype.md)</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.landmarktypeproperty">LandmarkTypeProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getlandmarktype">GetLandmarkType</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setlandmarktype">SetLandmarkType</a></li></ul>|
| Level | Gets or sets a 1-based integer that describes the location of an element inside hierarchical or broken hierarchical structures.<ul><li>Type: int</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.levelproperty">LevelProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getlevel">GetLevel</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setlevel">SetLevel</a></li></ul>|
| LiveSetting | Gets or sets the live setting value  for the specified element.<ul><li>Type: [AutomationLiveSetting](../microsoft.ui.xaml.automation.peers/automationlivesetting.md)</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.livesettingproperty">LiveSettingProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getlivesetting">GetLiveSetting</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setlivesetting">SetLiveSetting</a></li></ul>|
| LocalizedControlType | Gets or sets a localized text string that describes the type of control that the automation element represents.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.localizedcontroltypeproperty">LocalizedControlTypeProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getlocalizedcontroltype">GetLocalizedControlType</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setlocalizedcontroltype">SetLocalizedControlType</a></li></ul>|
| LocalizedLandmarkType | Gets or sets a localized text string that describes the type of landmark that the automation element represents.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.localizedlandmarktypeproperty">LocalizedLandmarkTypeProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getlocalizedlandmarktype">GetLocalizedLandmarkType</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setlocalizedlandmarktype">SetLocalizedLandmarkType</a></li></ul>|
| Name | Gets or sets the UI Automation name of the element.<ul><li>Type: string</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.nameproperty">NameProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getname">GetName</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setname">SetName</a></li></ul>|
| PositionInSet | Gets or sets a 1-based integer that describes the ordinal location of the element within a set of elements that are considered to be siblings.<ul><li>Type: int</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.positioninsetproperty">PositionInSetProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getpositioninset">GetPositionInSet</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setpositioninset">SetPositionInSet</a></li></ul>|
| SizeOfSet | Gets or sets the number of elements in a set of elements that are considered to be siblings.<ul><li>Type: int</li><li>Identifier field: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.sizeofsetproperty">SizeOfSetProperty</a></li><li>Accessor methods: <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.getsizeofset">GetSizeOfSet</a>, <a href="/uwp/api/windows.ui.xaml.automation.automationproperties.setsizeofset">SetSizeOfSet</a></li></ul>|

### Version history

| Windows version | SDK version | Value added |
| -- | -- | -- |
| 1511 | 10586 | GetLandmarkType |
| 1511 | 10586 | GetLocalizedLandmarkType |
| 1511 | 10586 | SetLandmarkType |
| 1511 | 10586 | SetLocalizedLandmarkType |
| 1607 | 14393 | GetDescribedBy |
| 1607 | 14393 | GetFlowsFrom |
| 1607 | 14393 | GetFlowsTo |
| 1607 | 14393 | GetFullDescription |
| 1607 | 14393 | GetIsDataValidForForm |
| 1607 | 14393 | GetIsPeripheral |
| 1607 | 14393 | GetLocalizedControlType |
| 1607 | 14393 | SetFullDescription |
| 1607 | 14393 | SetIsDataValidForForm |
| 1607 | 14393 | SetIsPeripheral |
| 1607 | 14393 | SetLocalizedControlType |
| 1703 | 15063 | GetCulture |
| 1703 | 15063 | SetCulture |
| 1803 | 17134 | GetHeadingLevel |
| 1803 | 17134 | SetHeadingLevel |
| 1809 | 17763 | GetIsDialog |
| 1809 | 17763 | SetIsDialog |

## -examples

## -see-also
[Accessibility](/windows/uwp/accessibility/accessibility), [Basic accessibility information](/windows/uwp/accessibility/basic-accessibility-information), [Accessibility testing](/windows/uwp/accessibility/accessibility-testing), [Attached properties overview](/windows/uwp/xaml-platform/attached-properties-overview), [Code samples for resolving common programmatic accessibility issues in Windows desktop apps](/accessibility-tools-docs/)
