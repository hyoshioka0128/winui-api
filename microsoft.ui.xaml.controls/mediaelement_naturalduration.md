---
-api-id: P:Microsoft.UI.Xaml.Controls.MediaElement.NaturalDuration
-api-type: winrt property
---

<!-- Property syntax
public Windows.UI.Xaml.Duration NaturalDuration { get; }
-->

# Microsoft.UI.Xaml.Controls.MediaElement.NaturalDuration

## -description
Gets the duration of the media file currently opened.

## -property-value
The natural duration of the media. The default value is a [Duration](../microsoft.ui.xaml/duration.md) structure that evaluates as [Automatic](../microsoft.ui.xaml/durationhelper_automatic.md), which is the value held if you query this property before [MediaOpened](mediaelement_mediaopened.md).

## -remarks
A [Duration](../microsoft.ui.xaml/duration.md) value has a **TimeSpan** component.

> **C# or Microsoft Visual Basic**
> You can use utility methods of **System.TimeSpan** to get the duration components in whatever format you want. For example you can get [TimeSpan.Hours](/dotnet/api/system.timespan.hours?redirectedfrom=MSDN#System_TimeSpan_Hours), [TimeSpan.Minutes](/dotnet/api/system.timespan.minutes?redirectedfrom=MSDN#System_TimeSpan_Minutes) and [TimeSpan.Seconds](/dotnet/api/system.timespan.seconds?redirectedfrom=MSDN#System_TimeSpan_Seconds) separately.



> **Visual C++ component extensions (C++/CX)**
> The data value of a [Duration](../microsoft.ui.xaml/duration.md) is a property named **TimeSpan**. This has a [TimeSpan](/uwp/api/windows.foundation.timespan) structure value, and that structure has a field named **Duration** that reports the duration as an **int64** that counts in 100-nanosecond units. [TimeSpan](/uwp/api/windows.foundation.timespan) doesn't have any methods for getting components of the time in *hours:minutes:seconds* format.

For more info, see Remarks in the [Duration](../microsoft.ui.xaml/duration.md) reference topic.

## -examples

## -see-also
