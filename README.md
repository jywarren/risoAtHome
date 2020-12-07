# riso@home
Web-based tools for printing separated colors w/ halftone on a home laser printer

Risograph printers (and other print processes that use halftone color effects) create beautiful layered patterns of colored dots to achieve a full range of colors from just 4 inks -- or even fewer, with creative color mixing. This typically uses [color halftone](https://en.wikipedia.org/wiki/Halftone#Multiple_screens_and_color_halftoning) techniques, but sometimes also [dithering](https://en.wikipedia.org/wiki/Dithering). 

We don't have a risograph printer, but want to do some home publishing, and got a $270 laser printer. Here are some tools to do fun color work with a laser printer!

We use web-based [Image Sequencer](https://sequencer.publiclab.org) to generate a color halftone version of any image you drag onto the page. Also check out the amazing https://antiboredom.github.io/p5.riso/ by Sam Lavigne and Tega Brain for ways to do a lot of this in [p5js](https://p5js.org)!

Here's a sample of what this process can look like when printed on a laser printer in multiple passes:

![Printed magpie](https://jywarren.github.io/risoAtHome/examples/magpie-printed.jpg)

Here's an example of color halftone in a digital image; left is the original picture, and right is the color halftone version:

![Toddler Jeff](https://jywarren.github.io/risoAtHome/examples/jeff-2up.jpg)


## Color separation and halftone

Each of these four sequences generates a different color plate. Drop your image into each to get 4 different layers to print onto the same page. Print 4 times on the same sheet to get some nice mis-alignment (registration error)!

> <a href="https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},dynamic{green:255|blue:255}">Cyan</a>

> <a href="https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},dynamic{red:255|blue:255}">Magenta</a>

> <a href="https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},dynamic{red:255|green:255}">Yellow</a>

> <a href="https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},threshold{input:1})">Black (optional, see below)</a>

Alternatively, try this black channel separator to skip halftoning and increase contrast, for example to better capture a clean black text or linework channel:

> <a href="https://sequencer.publiclab.org/examples/#steps=contrast{},threshold{input:1}">Black w no halftone</a>

Here's what an image of a magpie looks like separated into these 4 channels ([click here](https://jywarren.github.io/risoAtHome/examples/magpie-4-full.png) to see full res versions):

![CMYK magpie](https://jywarren.github.io/risoAtHome/examples/magpie-4.jpg)

And here's the original magpie painting: 

![CMYK magpie](https://jywarren.github.io/risoAtHome/examples/magpie.jpg)

See more photos of this, plus process photos, here: https://photos.app.goo.gl/1P8sER9eWqRHMkZW9

## Quick version

To generate a single image you can print in just one pass, you can just use this sequence, which creates a single RGB image with all four color halftone channels. Because it's an RGB image, you won't get rich (4-color) black, or any color blending in black regions (see below). You also won't get any registration errors. But it's a much faster process, of course!

> https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3}

This ends up looking like this:

![RGB magpie](https://jywarren.github.io/risoAtHome/examples/magpie-rgb.png)


### Printing black

Note that the black sequence above just thresholds out any non-black values, to generate a channel that is all values in the image which are completely black. This will essentially be all areas which have C+M+Y all present. Skipping this black channel is OK - C+M+Y will form a very dark shade that reads nicely as black, but if you want to add an extra oomph to your black, you can add this on top.

We're not sure if pre-separating black shades would be cleaner. Could be worth a try! Especially if you have **text or linework you don't want to halftone,** you could print the black layer solid (no halftoning) to achieve that. 

Note that by printing each layer separately, the printer will actually give you composite black (C+M+Y) which is not jet black, or if you print the K channel separately, it can even give you "rich black" which is C+M+Y+K. 

If you print the "Quick version" above, anywhere that is composite black (C+M+Y) will get rendered as K by many (most?) printers. That's one reason that the single-pass "Quick" approach is not as nice looking; where all three colors are present, there is actually no mixing happening, as there would be on a real 4-color process, as those regions get converted to flat black.

There are lots of tricks and techniques for printing or not printing black. You can [redistribute the black channel among the 3 other colors](https://www.brainbell.com/tutorials/Photoshop/Changing_A_Four-Color_Image_To_Three_Colors.htm), for example; we'd love to make a sequence for that too!

![Registration errors](https://jywarren.github.io/risoAtHome/examples/registration.jpg)

### Registration errors

Registration errors occur when the color plates don't align, causing beautiful swaths of cyan, magenta, or yellow to spill out around the edges of shapes. It can also cause some interesting moire effects if the halftones aren't angled away from each other enough (usually C, M, and K -- black -- are rotated by specific distinct angles to avoid interference patterns).

To get this effect, we've just run the print through the printer once for each color channel, printing separately. Our laser printer doesn't perfectly align each print, especially when we load through the manual feed tray, so it looks great. We are also thinking of intentionally introducing offset (rotation and translation) so that this can be achieved with a single print pass, but it's a little more contrived and the image sequence would be more complex.

## Ideas to add later

* introduce random registration offsets/rotations between channels for single-image "Quick" version
* try a dithering version
