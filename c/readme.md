# rpi_multichannel_ws281x


It uses the secondary memory interface (SMI) of the RaspberryPi to generate accurate signals.
The SMI is said to be capable of using 18 channels, but the article only shows 8 or 16 channels. The SMI bus signals are SD0~SD17 and are assigned to GPIOs 8~25.




# origin
fork from https://github.com/jbentham/rpi
( original repository detail as : https://iosoft.blog for details )


# Some Tips I have looked into this

https://qiita.com/nanbuwks/items/76c6ead17a469b57051b
「RaspberryPi で WS281X LEDストリップをマルチチャンネル駆動する」

# rpi_8chwave

I modified the original to make it easier to control monochromatic waves.

ex.,

```

 $ sudo ./rpi_8chwave -n 100 -w 100 -B 10 FF0000 00FF00 0000FF FFFF00 00FFFF FF00FF 808080 FFFFFF 

```

red,green,blue,yellow,cyan,masenta,gray,white wave with 100ms wait


wave pattern give wave_pattern on  rpi_8chwave.c
```
int wave_pattern[8][16] = {
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0},
          {0,10,30,50,70,80,90,100,100,90,80,70,50,30,10,0}
                          };
```

It's make 1 wavelength with 16 LED stream,
with brightness: 0%,10%,30%,50%,70%,80%,90%,100%,100%,90%,80%,70%,50%,30%,10%,0%.

## option 

- -n LED number each channel
- -w loop wait (ms)
- -B Brightness (0-100%)
- -G use GRB signal out (default : RGB signal )

