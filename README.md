# LedTableSimulator
Simulation frontend for a 10 x 10 RGB Pixel Led Table

This Repository contains a platform agnostic UI frontend that visualizes a 10 x 10 RGB LED Matrix LedTable.

Requirements:
1. The UI should be as platform independend as possible (at least MacOS, Linux and Windows should be supported, Bonus points for Android and iOS)
2. The UI should contain a 10 x 10 LED Pixel Matrix with rather huge pixels (lets say 64x64 screen pixels for one LED pixel)
3. The Simulator should receive the pixel values to be shown based on the following specification:
  - Each pixel is represented bye 3 Bytes
  - Each byte in a single pixel datum represents a single color value (0 - 255 where 0 is off, and 255 is maximum brightness)
  - The color order of each pixel is BGR (blue, green red)
  - The pixel values for the whole table are represented as a byte array of size 10 x 10 x 3 bytes.
4. The pixel data array of point 3.d is named framebuffer from now on
5. The Simulator should receive the framebuffer via MQTT by subscribing to the topic ledtable/simulation/framebuffer
6. Whenever the framebuffer is received via mqtt - the UI should update its state based on the framebuffer content
7. The pixel order inside the framebuffer is as follows (snake pattern):
  - Width is 10 pixels - refered to by W
  - Height is 10 pixel - refered to by H
  - X and Y are coordinates on the table where x = 0 is the very left and y = 0 is the very bottom of the table.
  - Pixel order is x0y0 .. x0yH, x1yH .. x1y0, x2y0 .. x2yH, x3yH ..x3y0 .. further to the right until xW
