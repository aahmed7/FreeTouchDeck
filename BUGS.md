# BUGS

Following problems need to be addressed manually.

## 1. Adafruit library can't find Adafruit_I2CDevice.h

Comment in Adafruit_GFX.cpp. I am using an SPI LCD so not an issue.

## 2. mbedtls function names have changed

Change these three lines in WebAuthentication.cpp:

```C
  mbedtls_md5_starts(&_ctx);
  mbedtls_md5_update(&_ctx, data, len);
  mbedtls_md5_finish(&_ctx, _buf);
```

To:

```C
  mbedtls_md5_starts_ret(&_ctx);
  mbedtls_md5_update_ret(&_ctx, data, len);
  mbedtls_md5_finish_ret(&_ctx, _buf);
```

Ref: [https://github.com/philbowles/ESPAsyncWebServer/issues/3]
