# Seven Segment OCR for PHP
A wrapper to work with Seven Segment OCR for PHP.
This wrapper is adoption from the one built for Tesseract OCR [Tesseract OCR for PHP](https://github.com/thiagoalessio/tesseract-ocr-for-php).

## Installation
You first need to make sure you have installed OCR library for seven segment number [SSOCR](https://github.com/auerswal/ssocr) by auerswal.

To use this library,
```
$ composer require aanred/ssocr-for-php
```

## Quick Start and Examples
Basic Usages,
```php
$ssocr = new SSOCR('img.png');
echo $ssocr->run();
```

Examples,

Monochrome image ([004200_mono.png](https://github.com/aanred/ssocr-for-php/blob/master/img/004200_mono.png))

![Monochrome](https://github.com/aanred/ssocr-for-php/blob/master/img/004200_mono.png)

```php
$ssocr = new SSOCR('004200_mono.png');
echo $ssocr->run();
// Result
// 004200
```

Coloured image ([004200.png](https://github.com/aanred/ssocr-for-php/blob/master/img/004200.png))

![Coloured](https://github.com/aanred/ssocr-for-php/blob/master/img/004200.png)

```php
$ssocr = new SSOCR('004200.png');
// use iterative thresholding
$ssocr->iterativeThreshold();
// we need to crop the image so the tiny dot on the right bottom corner is not processed
$ssocr->crop(0, 0, 598, 172);
echo $ssocr->run();
// Result
// 004200
```

Manual threshold ([inside_box.png](https://github.com/aanred/ssocr-for-php/blob/master/img/inside_box.png))

![Threshold](https://github.com/aanred/ssocr-for-php/blob/master/img/inside_box.png)

```php
$ssocr = new SSOCR('inside_box.png');
// use manual thresholding
$ssocr->threshold(20);
// we need to crop the image to take only the boxed numbers
$ssocr->crop(230, 195, 220, 60);
echo $ssocr->run();
// Result
// 086861
```
