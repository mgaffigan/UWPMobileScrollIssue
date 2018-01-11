Example demonstrating an issue which occludes the focused text box when using Windows Enterprise Handheld 10 with UWP.

## Scenario

Issue appears to happen whenever the `Page` with a `BottomAppBar` is displaced in the layout from the root visual.  This can be caused by a `Margin` or `Padding` on a wrapper element.

Broken visual tree:

- `Window.Current.Content` `Frame` 
 - `Border` with 1px `Margin`
  - `ContentPresenter`
   - `Page`

## Repro

1.	Start the app
2.  Touch one of the bottom text boxes that are below where the SIP will appear
3.	Note that the textbox touched is now hidden behind the `BottomAppBar`
4.  For a workaround, recompile with the `WORKAROUND` define and observe that the textbox remains above the `BottomAppBar`
5.	To avoid the bug, edit App.xaml to set the `Border.Padding` to 0