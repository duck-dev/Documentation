# Selectors

## OfType <a id="oftype"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="Button">
<Style Selector="local|Button">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<Button>());
new Style(x => x.OfType(typeof(Button)));
```
{% endtab %}
{% endtabs %}

Selects a control by type. The first example above selects the `Avalonia.Controls.Button` class. To include a XAML namespace in the type separate the namespace and the type with a `|` character.

This selector does not match derived types. For that, use the [`Is`](selectors.md#is) selector.

> Note the type of an object is actually determined by looking at its IStyleable.StyleKey property. By default this simply returns the type of the current instance, but if, for example, you do want your control which inherits from `Button` to be styled as a `Button`, then you can implement the `IStyleable.StyleKey` property on your class to return `typeof(Button)`.

## Name <a id="name"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="#myButton">
<Style Selector="Button#myButton">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.Name("myButton"));
new Style(x => x.OfType<Button>().Name("myButton"));
```
{% endtab %}
{% endtabs %}

Selects a control by its [`Name`](http://reference.avaloniaui.net/api/Avalonia/StyledElement/2362746E) property.

## Class <a id="class"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="Button.large">
<Style Selector="Button.large:focus">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<Button>().Class("large"));
new Style(x => x.OfType<Button>().Class("large").Class(":focus"));
```
{% endtab %}
{% endtabs %}

Selects a control with the specified style classes. Multiple classes should be separated with a `.` character, or a `:` character in the case of pseudoclasses. If multiple classes are specified then the control must have all of the requested classes present in order to match.

## Is <a id="is"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector=":is(Button)">
<Style Selector=":is(local|Button)">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.Is<Button>());
new Style(x => x.Is(typeof(Button)));
```
{% endtab %}
{% endtabs %}

This is very similar to the [`OfType`](selectors.md#ofType) selector except it also matches derived types.

> Again, the type of an object is actually determined by looking at its IStyleable.StyleKey property.

## Child <a id="child"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="StackPanel > Button">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<StackPanel>().Child().OfType<Button>());
```
{% endtab %}
{% endtabs %}

A child selector is defined by separating two selectors with a `>` character. This selector matches _direct children in the logical tree_, so in the example above the selector will match any `Button` that is a direct logical child of a `StackPanel`.

## Descendant <a id="descendant"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="StackPanel Button">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<StackPanel>().Descendant().OfType<Button>());
```
{% endtab %}
{% endtabs %}

When two selectors are separated by a space, then the selector will match descendants in the logical tree, so in this case the selector will match any `Button` that is a logical descendant of a `StackPanel`.

## PropertyEquals <a id="propertyequals"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="Button[IsDefault=true]">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<Button>().PropertyEquals(Button.IsDefaultProperty, true));
```
{% endtab %}
{% endtabs %}

Matches any control which has the specified property set to the specified value.

## Template <a id="template"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="Button /template/ ContentPresenter">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<Button>().Template().OfType<ContentPresenter>());
```
{% endtab %}
{% endtabs %}

Matches a control in a control template. All other selectors listed here work on the logical tree. If you wish to select a control in a control template then you must use this selector. The example selects `ContentPresenter` controls in the templates of `Button`s.

## Not <a id="not"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="TextBlock:not(.h1)">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<TextBlock>().Not(y => y.Class("h1")));
```
{% endtab %}
{% endtabs %}

Negates an inner selector.

## Nth Child <a id="nth-child"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="TextBlock:nth-child(2n+3)">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<TextBlock>().NthChild(2, 3));
```
{% endtab %}
{% endtabs %}

Matches elements based on their position in a group of siblings.


## Nth Last Child <a id="nth-last-child"></a>

{% tabs %}
{% tab title="XAML" %}
```markup
<Style Selector="TextBlock:nth-last-child(2n+3)">
```
{% endtab %}

{% tab title="C\#" %}
```csharp
new Style(x => x.OfType<TextBlock>().NthLastChild(2, 3));
```
{% endtab %}
{% endtabs %}

Matches elements based on their position among a group of siblings, counting from the end.
