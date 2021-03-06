# ListViewBaseExtensions class

ListViewBaseExtensions provides extension method that allow attaching ICommand to handle ListViewBase Item interaction by means of [ItemClick](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.listviewbase.itemclick.aspx) event. 
ListViewBase [IsItemClickEnabled](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) must be set to **true**



## Example

```xml
    // Attach the command declared in MainViewModel to ListView declared in XAML
    // IsItemClickEnabled is set to true as shown below
    <ListView
        ui:ListViewBaseExtensions.Command="{x:Bind MainViewModel.ItemSelectedCommand, Mode=OneWay}"
        IsItemClickEnabled="True"
        ItemsSource="{x:Bind MainViewModel.Items, Mode=OneWay}"
        SelectionMode="None" />
```

<br/>
The AlternateColor property provides a way to assign a background color to every other item.

> The <a href="https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.listviewbase#Windows_UI_Xaml_Controls_ListViewBase_ContainerContentChanging" target="_blank">ContainerContentChanging</a> event used for this extension to work, will not be raised when the ItemsPanel is replaced with another type of panel than ItemsStackPanel or ItemsWrapGrid. 

## Example

```xml
    <ListView
        ui:ListViewBaseExtensions.AlternateColor="Silver"
        ItemsSource="{x:Bind MainViewModel.Items, Mode=OneWay}" />
```

<br/>
The AlternateItemTemplate property provides a way to assign an alternate <a href="https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.datatemplate" target="_blank">datatemplate</a> to every other item. It is also possible to combine with the AlternateColor property.

> The <a href="https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.listviewbase#Windows_UI_Xaml_Controls_ListViewBase_ContainerContentChanging" target="_blank">ContainerContentChanging</a> event used for this extension to work, will not be raised when the ItemsPanel is replaced with another type of panel than ItemsStackPanel or ItemsWrapGrid. 

## Example

```xml
    <Page.Resources>
        <DataTemplate x:Name="NormalTemplate">
            <TextBlock Text="{Binding }" Foreground="Green"></TextBlock>
        </DataTemplate>
        
        <DataTemplate x:Name="AlternateTemplate">
            <TextBlock Text="{Binding }" Foreground="Orange"></TextBlock>
        </DataTemplate>
    </Page.Resources>

    <ListView
        ItemTemplate="{StaticResource NormalTemplate}"
        ui:ListViewBaseExtensions.AlternateItemTemplate="{StaticResource AlternateTemplate}"
        ItemsSource="{x:Bind MainViewModel.Items, Mode=OneWay}" />
```

## Requirements (Windows 10 Device Family)

| [Device family](http://go.microsoft.com/fwlink/p/?LinkID=526370) | Universal, 10.0.10586.0 or higher |
| --- | --- |
| Namespace | Microsoft.Toolkit.Uwp.UI |

## API

* [ListViewBaseExtensions source code](https://github.com/Microsoft/UWPCommunityToolkit/blob/dev/Microsoft.Toolkit.Uwp.UI/Extensions/ListViewBaseExtensions.cs)

