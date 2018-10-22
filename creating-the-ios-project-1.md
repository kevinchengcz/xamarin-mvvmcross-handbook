# Creating the iOS project

Add an iOS App \(Xamarin\) project called `MvvmCrossDemo.Forms.iOS` into the solution, like this:

![](.gitbook/assets/image%20%2851%29.png)

Note that do not use iOS XAML App \(Xamarin.Forms\) template. Use the Blank App template and select it for iPhone:

![](.gitbook/assets/image%20%2834%29.png)

Then install the `Xamarin.Forms` package to the project through the NuGet Package Manager:

![](.gitbook/assets/image%20%286%29.png)

Or install it by the command below in the NuGet Manager Console:

```bash
Install-Package Xamarin.Forms
```

Install the `MvvmCross.Forms` package in the NuGet Package Manager:

![](.gitbook/assets/image%20%281%29.png)

Or you can install it by the command below in the NuGet Manager Console:

```bash
Install-Package MvvmCross.Forms 
```

Like the Android project, add the reference to the `MvvmCrossDemo.Core` project and the `MvvmCrossDemo.Forms.UI` project. Update the default namespace of the `MvvmCrossDemo.Forms.iOS` project to `MvvmCrossDemo.Forms.iOS` instead of `Blank`, like this:

![](.gitbook/assets/image%20%284%29.png)

Open the `AppDelegate.cs` file and update the class to inherit from `MvxFormsApplicationDelegate<MvxFormsIosSetup<Core.App, UI.App>, Core.App, UI.App>` instead of `UIApplicationDelegate`. Then delete all the pre-populated methods in the `AppDelegate` class, as shown below:

```csharp
using Foundation;
using MvvmCross.Forms.Platforms.Ios.Core;

namespace MvvmCrossDemo.Forms.iOS
{
    // The UIApplicationDelegate for the application. This class is responsible for launching the
    // User Interface of the application, as well as listening (and optionally responding) to application events from iOS.
    [Register("AppDelegate")]
    public class AppDelegate : MvxFormsApplicationDelegate<MvxFormsIosSetup<Core.App, UI.App>, Core.App, UI.App>
    {
       
    }
}
```

You can find the sample code of it here: [https://github.com/MvvmCross/MvvmCross/blob/develop/ContentFiles/Forms/iOSContent/AppDelegate.cs.pp](https://github.com/MvvmCross/MvvmCross/blob/develop/ContentFiles/Forms/iOSContent/AppDelegate.cs.pp).

That is it! All the Views of the iOS project are handled by the `MvvmCrossDemo.Forms.UI` project so we can reuse a lot of codes between these projects.
