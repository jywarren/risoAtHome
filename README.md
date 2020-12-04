# risoAtHome
Web-based tools for printing separated colors w/ halftone on a home laser printer


We use web-based [Image Sequencer](https://sequencer.publiclab.org) to generate a color halftone version of any image you drag onto the page.

Each of these four sequences generates a different color plate. Drop your image into each to get 4 different layers to print onto the same page. Print 4 times on the same sheet to get some nice mis-alignment (registration error)!

> **Cyan:** https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},dynamic{green:255|blue:255}

> **Magenta:** https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},dynamic{red:255|blue:255}

> **Yellow:** https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},dynamic{red:255|green:255}

> **Black:** https://sequencer.publiclab.org/examples/#steps=brightness{brightness:100},color-halftone{angle:1|size:3},threshold{input:1}


### About the black plate

Note that black just thresholds out any non-black values. We're not sure if pre-separating black shades would be cleaner. Could be worth a try! Especially if you have text or linework you don't want to halftone, you could print the black layer solid to achieve that. 

Note that by printing each layer separately, the printer will actually give you composite black (C+M+Y) which is not jet black, or if you print the K channel separately, it can even give you "rich black" which is C+M+Y+K. 

### 

## Quick riso

To generate a single image you can print, you can just use this sequence, which creates a single RGB image with all four color halftone channels. But, because it's an RGB image, you won't get rich black (see above).

