## What is OpenMacroBoard
OpenMacroBoard provides a few libraries that help you implement custom functionality for various
macro boards (with focus on devices with key displays, like the Stream Deck or Stream Deck Mini).
At the moment OpenMacroBoard is for developers only and there is no easy-to-use
software or installer - just a bunch of libraries ;-)

## Getting started
To start developing you need [`OpenMacroBoard.SDK`](https://www.nuget.org/packages/OpenMacroBoard.SDK/) and
the provider(s) you like. Providers are libraries that manage the communication to the macro boards.
This abstraction is needed to allow third parties to implement devices without changes to the core functionality.

To try things out, create a new console application (>= .Net 4.0), add
the nuget package [`OpenMacroBoard.VirtualBoard`](https://www.nuget.org/packages/OpenMacroBoard.VirtualBoard/)
(OpenMacroBoard.SDK will be downloaded as dependency automatically) and copy/paste the following lines:

```c#
using(var device = BoardFactory.SpawnVirtualBoard())
{
    var redKey = KeyBitmap.Create.FromRgb(255,0,0);
    device.SetKeyBitmap(redKey);
    Console.ReadKey();
}
```

If you want to run your program on a real device, you can
add another provider (for example [`StreamDeckSharp`](https://www.nuget.org/packages/StreamDeckSharp/)).

## Providers
At the moment there are just two providers, with a total of three supported devices.

| Device	| Provider	| Description	|
| ---	| ---	| ---	|
| [Stream Deck](https://www.elgato.com/de/gaming/stream-deck)<sup>1</sup>	| [`StreamDeckSharp`](https://www.nuget.org/packages/StreamDeckSharp/)	| 5x3 by Elgato	|
| [Stream Deck Mini](https://www.elgato.com/de/gaming/stream-deck-mini)<sup>1</sup>	| [`StreamDeckSharp`](https://www.nuget.org/packages/StreamDeckSharp/)	| 3x2 by Elgato	|
| VirtualBoard	| [`OpenMacroBoard.VirtualBoard`](https://www.nuget.org/packages/OpenMacroBoard.VirtualBoard/)	| Software emulated board with arbitrary key configuration	|

<sup>1</sup> _Not officially supported by the manufacturer, but thrid party implementations_

We'd love to add more. You can implement it by yourself if you are a developer by referencing
[`OpenMacroBoard.SDK`](https://www.nuget.org/packages/OpenMacroBoard.SDK/) and write a method that returns an IMacroBoard.
If want me to implement it, you can donate hardware (or the money so I can buy that specific hardware
you want implemented) - just create a ticket and we talk about it ;-)

## Examples
You can find a lot of examples in our [example collection](https://github.com/OpenMacroBoard/OpenMacroBoard.ExampleCollection)

Here are a few impressions

![Lasershow on StreamDeck](/assets/images/lasershow.png)

[![Demo video of the example](https://i.imgur.com/8tlkaIg.png)](http://www.youtube.com/watch?v=tNwUG0sPmKw)  
_*The glitches you can see are already fixed._

## Plans for the future
I'd like to write an open source alternative for the elgato stream deck software that supports more
devices and lets developers write functions/plugins/widgets for all devices with an existing `IMacroBoard` provider.
If you want to help feel free to contact me (just create a ticket or send me a mail).

## Details
For more details and information please visit the [github repositories](https://github.com/OpenMacroBoard).
