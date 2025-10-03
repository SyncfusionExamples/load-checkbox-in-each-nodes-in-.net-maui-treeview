# load-checkbox-in-each-nodes-in-.net-maui-treeview
This repository demonstrates how to display a checkbox in each node of the .NET MAUI TreeView (SfTreeView) control. It provides a sample implementation that enables recursive checkbox selection, data binding for checked states, and collection tracking of checked items, allowing users to easily select and manage multiple nodes in a hierarchical structure.

## Sample

### XAML

```xaml
<ContentPage.BindingContext>
        <local:FileManagerViewModel x:Name="fileManagerViewModel"/>
    </ContentPage.BindingContext>

    <treeview:SfTreeView x:Name="treeView"
                        ItemsSource="{Binding Folders}"
                        AutoExpandMode="AllNodesExpanded"
                        CheckBoxMode="Recursive"
                        ItemTemplateContextType="Node"
                        CheckedItems="{Binding CheckedItems}"
                        NodePopulationMode="Instant"
                        SelectionMode="None">

        <treeview:SfTreeView.HierarchyPropertyDescriptors>
            <treeviewengine:HierarchyPropertyDescriptor TargetType="{x:Type local:Folder}" ChildPropertyName="FilesInfo"/>
            <treeviewengine:HierarchyPropertyDescriptor TargetType="{x:Type local:File}" ChildPropertyName="SubFiles"/>
        </treeview:SfTreeView.HierarchyPropertyDescriptors>
        
        <treeview:SfTreeView.ItemTemplate >
            <DataTemplate>
                <Grid>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="40" />
                        <ColumnDefinition Width="40" />
                        <ColumnDefinition Width="*" />
                    </Grid.ColumnDefinitions>
                    <Grid Grid.Column="0" >
                        <checkbox:SfCheckBox VerticalOptions="Center"
                                             HorizontalOptions="Center"
                                             IsThreeState="True"   
                                             IsChecked="{Binding IsChecked, Mode=TwoWay}"/>
                    </Grid>
                    <Grid Grid.Column="1">
                        <Image Source="{Binding Content.ImageIcon}"
                               VerticalOptions="Center"
                               HorizontalOptions="Center"
                               HeightRequest="24" 
                               WidthRequest="24"/>
                    </Grid>
                    <Grid Grid.Column="2" RowSpacing="1" Padding="1,0,0,0" VerticalOptions="Center">
                        <Label LineBreakMode="NoWrap"
                               Margin="5,0,0,0"
                               Text="{Binding Content.FolderName}"
                               CharacterSpacing="0.25" 
                               FontFamily="Roboto-Regular" 
                               FontSize="14"
                               VerticalTextAlignment="Center" />
                    </Grid>
                </Grid>
            </DataTemplate>
        </treeview:SfTreeView.ItemTemplate>
    </treeview:SfTreeView>
```

## Requirements to run the demo

To run the demo, refer to [System Requirements for .NET MAUI](https://help.syncfusion.com/maui/system-requirements).

Make sure that you have the compatible versions of [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/ ) with the Dot NET MAUI workload and [.NET Core SDK 7.0](https://dotnet.microsoft.com/en-us/download/dotnet/7.0) or later version in your machine before starting to work on this project.

## Troubleshooting:
### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.

## License

Syncfusion® has no liability for any damage or consequence that may arise from using or viewing the samples. The samples are for demonstrative purposes. If you choose to use or access the samples, you agree to not hold Syncfusion® liable, in any form, for any damage related to use, for accessing, or viewing the samples. By accessing, viewing, or seeing the samples, you acknowledge and agree Syncfusion®'s samples will not allow you seek injunctive relief in any form for any claim related to the sample. If you do not agree to this, do not view, access, utilize, or otherwise do anything with Syncfusion®'s samples.
