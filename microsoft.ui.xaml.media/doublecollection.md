---
-api-id: T:Microsoft.UI.Xaml.Media.DoubleCollection
-api-type: winrt class
---

<!-- Class syntax.
public class DoubleCollection : Windows.Foundation.Collections.IIterable<System.Double>, Windows.Foundation.Collections.IVector<System.Double>
-->

# Microsoft.UI.Xaml.Media.DoubleCollection

## -description
Represents an ordered collection of [Double](/dotnet/api/system.double?redirectedfrom=MSDN) values.

## -remarks
<!--Begin NET note for IEnumerable support-->
### Enumerating the collection in C# or Microsoft Visual Basic

A DoubleCollection is enumerable, so you can use language-specific syntax such as **foreach** in C# to enumerate the items in the collection. The compiler does the type-casting for you and you won't need to cast to `IEnumerable<Double>` explicitly. If you do need to cast explicitly, for example if you want to call [GetEnumerator](/dotnet/api/system.collections.ienumerable.getenumerator), cast to [IEnumerable<T>](/dotnet/api/system.collections.generic.ienumerable-1) with a [Double](/dotnet/api/system.double?redirectedfrom=MSDN) constraint.


<!--End NET note for IEnumerable support-->

## -examples

## -see-also
[IVector&lt;T&gt;](/uwp/api/windows.foundation.collections.ivector`1), [IIterable&lt;T&gt;](/uwp/api/windows.foundation.collections.iiterable`1), [IList<T>](/dotnet/api/system.collections.generic.ilist-1)
