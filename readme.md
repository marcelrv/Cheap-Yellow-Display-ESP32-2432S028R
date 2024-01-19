# intro

This project is a platformio version of the test program(s) for the Adafruit ILI9341 library
applied to the ESP32-2432S028R board aka Cheap Yellow Display / CYD.

Sharing this as I had some initial hurdles getting this board to run with standard libraries

Key elements to get it working:

Use 2 SPI classes:
```
SPIClass hspi = SPIClass(HSPI);
SPIClass vspi = SPIClass(VSPI);

```

Initializes the touchscreen while passing the spiclass:
`Adafruit_ILI9341 tft = Adafruit_ILI9341(&hspi, TFT_DC, TFT_CS, TFT_RST);`

Setup the VSPI to use custom pins for the touch
  
```
vspi.begin(XPT2046_CLK, XPT2046_MISO, XPT2046_MOSI, XPT2046_CS);
ts.begin(vspi);
````