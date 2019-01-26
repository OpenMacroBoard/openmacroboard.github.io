## What is OpenMacroBoard
OpenMacroBoard provides a few libraries that help you implement custom functionality for various macro board (with focus on devices with key displays, like the Stream Deck or Stream Deck Mini). At the moment OpenMacroBoard is for developers only and there is no easy-to-use software or installer - just a bunch of libraries :wink:

## Getting started
To start developing you need `OpenMacroBoard.SDK` and the provider(s) you like. Providers are libraries that manage the communication to the macro boards. This abstraction is needed to allow third parties to implement devices without changes to the core functionality.

To try things out, create a new console application (>= .Net 4.0), add the nuget package [OpenMacroBoard.VirtualBoard](https://www.nuget.org/packages/OpenMacroBoard.VirtualBoard/) (`OpenMacroBoard.SDK` will be downloaded as dependency automatically) and copy/paste the following lines:

```c#
using(var device = BoardFactory.SpawnVirtualBoard())
{
    var redKey = KeyBitmap.Create.FromRgb(255,0,0);
    device.SetKeyBitmap(redKey);
    Console.ReadKey();
}
```

If you want to run your program on a real device, you can add another provider (for example [StreamDeckSharp](https://www.nuget.org/packages/StreamDeckSharp/)).

## Examples
You can find a lot of examples in our [example collection](https://github.com/OpenMacroBoard/OpenMacroBoard.ExampleCollection)

Here are a few impressions

![Lasershow on StreamDeck](/assets/images/lasershow.png)

## Plans for the future
I'd like to write an open source alternative for the elgato stream deck software that supports more devices and lets developers write functions/plugins/widgets for all devices with an existing `IMacroBoard` provider. If you want to help feel free to contact me (just create a ticket or send me a mail).

## Details
For more details and information please visit the [github repositories](https://github.com/OpenMacroBoard).
