# Default Style

## Idea

Every effect can be achieved in different ways in darktable. As a result, different photographers may achieve similar outcomes with entirely different tools. But on the other hand, any given photographer will develop his own methodology and find himself applying very similar processing to most pictures.

The idea of a *default style* is to save all the commonly used filters as separate style, which can be applied to more or less all (or at least many) pictures. This stile will not be perfect to any of them, but it shall serve as good starting point to otpimize results and hence save time.

## Variants

If you only shoot one style of pictures (e.g. only portrait) you may find *your default editing style*. If you shoot very different images, you may define multiple default styles for different types of images.

However, to keep things simple, in this repository the same default is used for all types of images and processing is optimized for every image from there.

## Examples

The table below shows the effect of the default style used (you can find it under [./Styles/Default.dtstyle](/Styles/Default.dtstyle)) on different types of images. Note that none of them is regarded as perfect and the default style is more meant as starting point for futher optimization specific to each image.

| Style         | Rider                                       | Mountain                                       | Portrait                                       |
| ------------- | ------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| Original      | ![Rider Original](./02_Rider/web/02.jpg)    | ![Rider Original](./06_Mountain/web/06.jpg)    | ![Rider Original](./05_Portrait/web/05.jpg)    |
| Default Style | ![Rider Original](./02_Rider/web/02_01.jpg) | ![Rider Original](./06_Mountain/web/06_01.jpg) | ![Rider Original](./05_Portrait/web/05_01.jpg) |



## Modules Used

This section will go through the different modules used in this style and shortly explain what they do and why they are there.

### Hot Pixels

The hot-pixels correction would fix errors caused by broken pixels of the sensor. In the example image chosen, there are not broken pixels. However, the hot pixels module shall always be enabled. Most cameras have a hand full of broken pixels.

The default values are used in the style as provided. In most cases they are working pretty well. 

![Hot Pixels](./DefaultStyle_HotPixels.png)

### Demosaic

The demosaic module controls the calculation of all color components for each pixel based on the bayered inputs. To explain this in a bit more detail, it may be important to know how image sensors work. In a nutshell, every pixel only detects one color (red, blue or green). For processing, all color components are required for each pixel. Therefore, the components not detected by the pixel directly, are calcluated based on neighbouring pixels. For example the blue and green components of a pixel that can only detect red are calculated on the neighbour pixels. This process is called *demosaicing*.

Because image processing happens offline, usually you want to focus on quality and not on processing speed. Therefore it is a good idea to chose the better quality *AMaZE* algorithm instead of the faster (and default) *PPG*. 

Usually default settings are okay. In high noise environments, you man want to add a bit of color smoothing. But for images taken at low or medium ISO settings, this certainly is not required and does not have a visible impact.

![Hot Pixels](./DefaultStyle_Demosaic.png)

### Denoise

