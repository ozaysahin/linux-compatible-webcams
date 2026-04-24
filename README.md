# 🎥 Linux UVC Uyumlu Generic Kameralar

> **UVC (USB Video Class)** — Linux kernel'ine dahil `uvcvideo` driver'ı sayesinde **sürücü kurmadan** çalışan kameraların listesidir.  
> Kaynak: [Linux UVC Driver & Tools](http://www.ideasonboard.org/uvc/)

---

## ⚠️ Önemli Notlar

| # | Uyarı |
|---|-------|
| [1] | 1. ve 2. nesil Logitech webcam'lerde firmware bug'ı var → kararsız davranışa yol açabilir. Yeni modelleri tercih et. |
| [2] | Linux kernel 2.6.22+ sürümünde USB audio bug fix, eski Logitech modellerde yeni bir bug tetikleyebilir. |
| [3] | Bazı notebook modellerde kamera **ters monte edilmiş** olabilir. `libv4l` kullanan uygulamalar bunu otomatik düzeltir. |
| [4] | Apple iSight webcam'ler için MacOS X driver'ından firmware çıkarılması gerekir. |
| [5] | USB 1.1 controller'a bağlandığında video bozulması yaşanabilir → USB 2.0'a bağla. |
| [6] | Bazı Logitech modellerinde belirli part number'larda [1]'e benzer sorunlar var. |
| [7] | Creative Live! Cam Video IM Pro'nun birden fazla versiyonu var; sadece biri UVC uyumlu. USB Product ID'yi kontrol et. |
| [8] | 640x480 altındaki çözünürlükler yalnızca 30fps'de çalışabilir. |
| [9] | Aynı Device ID birden fazla farklı kamera modeli tarafından kullanılıyor; satın almadan model adını doğrula. |
| [10] | USB 1.1 hub'a bağlandığında çalışmayabilir. |
| [11] | 1.3MP veya 2MP iddiasına rağmen UVC descriptor'ları maksimum 640x480 çözünürlük bildiriyor. |
| [12] | Bazı versiyonlar UVC'yi facade olarak kullanıyor; vendor protokolü ile gerçek işlem yapıyor → düşük FPS ve bozuk frame'lere yol açabilir. |
| [13] | Maksimum USB bandwidth talep ediyor; dahili mikrofon dahil başka USB cihazlarla aynı anda kullanımda sorun çıkabilir. |
| [14] | Varsayılan dışı frame rate'lerde düşük ışıkta aşırı karanlık görüntü. `RESTRICT_FRAME_RATE` quirk ile çözülebilir. |
| [15] | Bazı versiyonlarda UVC kontrol isteklerine random timeout/stall yaşanabiliyor. |
| [16] | Manuel exposure 2500/2^n dışında bir değere ayarlandığında görüntü aşırı parlak olabilir. |
| [17] | Tam çözünürlük tarama yalnızca still image capture ile mümkün; `uvcvideo` henüz desteklemiyor. |
| [18] | Linux kernel v2.3.37–v3.5 arasında USB auto-suspend sorunu olabilir. |

---

## 📋 Uyumlu Kamera Listesi

### ALi Corporation
| USB ID | Model | Notlar |
|--------|-------|--------|
| 0402:5606 | USB 2.0 Camera (VIT D2010 notebooks) | [12] |
| 0402:9665 | 1.3M WebCam (Acer Aspire AS7551-7442 notebooks) | |

### Quanta Computer
| USB ID | Model | Notlar |
|--------|-------|--------|
| 0408:030c | HP Webcam (HP Pavilion DV6744 ve DV6750) | |
| 0408:2fb1 | Laptop Integrated Webcam 2HDM (Dell XPS notebooks) | |

### Windbond
| USB ID | Model | Notlar |
|--------|-------|--------|
| 0416:a91a | LogiLink Wireless Webcam | |

### Creative Labs
| USB ID | Model | Notlar |
|--------|-------|--------|
| 041e:4057 | Creative Live! Cam Optia | |
| 041e:4058 | Creative Live! Cam Optia AF | [18] |
| 041e:4063 | Creative Live! Cam Video IM Pro | [7] |
| 041e:4065 | Creative Live! Cam Optia Pro | |
| 041e:406a | Creative Live! Cam Notebook Ultra | |
| 041e:406b | Creative Live! Cam Chat IM | |
| 041e:406c | Creative Live! Cam Sync | |
| 041e:4071 | Creative Live! Cam Vid. IM Ultra | |
| 041e:4080 | Creative Live! Cam Socialize HD | [16] |
| 041e:4088 | Creative Live! Cam Chat HD | |

### Genius
| USB ID | Model | Notlar |
|--------|-------|--------|
| 0458:505e | Genius iSlim 330 | |
| 0458:7055 | Genius iSlim 2020AF | |
| 0458:705d | Genius iSlim 2000AF | |
| 0458:706e | Genius eFace 2025 | |
| 0458:7070 | Genius FaceCam 310 | [13] |
| 0458:7071 | Genius iSlim 1300 V2 | |
| 0458:707c | Genius eFace 1300 | |
| 0458:7081 | Genius FaceCam 2000 | |

### Microsoft
| USB ID | Model | Notlar |
|--------|-------|--------|
| 045e:00f8 | Microsoft LifeCam NX-6000 | |
| 045e:0721 | Microsoft LifeCam NX-3000 | |
| 045e:074a | Microsoft LifeCam VX-500 | |
| 045e:075d | Microsoft LifeCam Cinema | [13] |
| 045e:076d | Microsoft LifeCam HD-5000 | |
| 045e:0770 | Microsoft LifeCam VX-700 | |
| 045e:0772 | Microsoft LifeCam Studio | [13][15] |
| 045e:0779 | Microsoft LifeCam HD-3000 | |

### Logitech
| USB ID | Model | Notlar |
|--------|-------|--------|
| 046d:0802 | Logitech Webcam C200 | |
| 046d:0804 | Logitech Webcam C250 | |
| 046d:0805 | Logitech Webcam C300 | |
| 046d:0807 | Logitech Webcam C500 | |
| 046d:0808 | Logitech Webcam C600 | |
| 046d:0809 | Logitech Webcam Pro 9000 | |
| 046d:080a | Logitech Portable Webcam C905 | |
| 046d:0819 | Logitech Webcam C210 | |
| 046d:081d | Logitech Webcam C310 | |
| 046d:0821 | Logitech Portable Webcam C910 | |
| 046d:0825 | Logitech HD Webcam C270 | |
| 046d:0826 | Logitech HD Webcam C525 | |
| 046d:082c | Logitech HD Webcam C615 | |
| 046d:082d | Logitech HD Pro Webcam C920 | |
| 046d:08c1 | Logitech Quickcam Fusion | [1][2] |
| 046d:08c2 | Logitech Quickcam Orbit/Sphere MP | [1][2] |
| 046d:08c3 | Logitech Quickcam for Notebooks Pro | [1][2] |
| 046d:08c5 | Logitech Quickcam Pro 5000 | [1][2] |
| 046d:08c6 | Logitech Quickcam OEM Dell Notebook | [1][2] |
| 046d:08c7 | Logitech Quickcam OEM Cisco VT Camera II | [1][2] |
| 046d:08c9 | Logitech Quickcam Ultra Vision | [1][2] |
| 046d:08ca | Logitech Quickcam Fusion (2006) | [1][2] |
| 046d:08cb | Logitech Quickcam for Notebooks Pro (2006) | [1][2] |
| 046d:08cc | Logitech Quickcam Orbit/Sphere MP (2006) | [1][2] |
| 046d:08ce | Logitech Quickcam Pro 5000 (2006) | [1][2] |
| 046d:0990 | Logitech Quickcam Pro 9000 / Pro 9000 for Business | [6] |
| 046d:0991 | Logitech Quickcam Pro for Notebooks (2007) | |
| 046d:0992 | Logitech Quickcam Communicate Deluxe | |
| 046d:0994 | Logitech Quickcam Orbit/Sphere AF | |
| 046d:09a1 | Logitech Quickcam Communicate MP/S5500 | |
| 046d:09a2 | Logitech Quickcam Communicate Deluxe/S7500 | |
| 046d:09a4 | Logitech Quickcam E 3500 | |
| 046d:09a5 | Logitech Quickcam 3000 for Business | |
| 046d:09a6 | Logitech Quickcam Vision Pro | |
| 046d:09b0 | Acer OrbiCam (Acer notebooks) | |
| 046d:09b2 | Fujitsu Webcam (Fujitsu-Siemens notebooks) | [3] |
| 046d:09c0 | Quickcam for Dell Notebooks | [1][2] |
| 046d:09c1 | Logitech Quickcam Deluxe for Notebooks | [1][2] |

### Philips
| USB ID | Model | Notlar |
|--------|-------|--------|
| 0471:0331 | Philips SPC 1300NC | |
| 0471:0332 | Philips SPC 1000NC | |
| 0471:0333 | Philips SPC 620NC | |
| 0471:0334 | Philips SPC 520/525NC | |
| 0471:2034 | Philips SPC 530NC | |
| 0471:2037 | Philips SPC 1330NC | |
| 0471:2038 | Philips SPC 2050NC | |
| 0471:20d0 | Philips SPZ2000 | |

### Sanyo Electric
| USB ID | Model | Notlar |
|--------|-------|--------|
| 0474:02da | Sanyo Xacti HD2000 | |
| 0474:0722 | Sanyo W33SA | |
| 0474:0b0e | Sanyo VPC-CA102 | |

### Chicony Electronics
| USB ID | Model | Notlar |
|--------|-------|--------|
| 04f2:a133 | Maxell MaxCam MWC-1300D | |
| 04f2:a13c | HP KQ246AA 8.0MP Deluxe Webcam | |
| 04f2:a13e | Panda 10C | |
| 04f2:b008 | Chicony USB 2.0 Camera | |
| 04f2:b012 | Chicony 1.3M UVC Webcam (Asus G1S) | [3] |
| 04f2:b013 | Chicony USB 2.0 Camera (Lenovo 3000 N200) | |
| 04f2:b015 | Chicony VGA 24fps UVC Webcam (HP) | |
| 04f2:b016 | Chicony VGA 30fps UVC Webcam (HP) | |
| 04f2:b018 | Chicony 2M UVC Webcam (Compal) | |
| 04f2:b021 | ViewSonic 1.3M Webcam (VX2255WMB) | [5] |
| 04f2:b022 | Gateway USB 2.0 Webcam (One C34xx) | |
| 04f2:b023 | Gateway USB 2.0 Webcam (HP Pavilion DV9560EG) | |
| 04f2:b024 | USB 2.0 Webcam (Packard Bell) | |
| 04f2:b027 | Gateway USB 2.0 Webcam (Gateway T-1616) | |
| 04f2:b029 | USB 2.0 1.3M UVC WebCam (Asus F6S) | [3] |
| 04f2:b033 | USB 2.0 1.3M UVC WebCam (Asus M70VM) | [3] |
| 04f2:b044 | Acer CrystalEye webcam (Acer Aspire 5535) | |
| 04f2:b062 | CNF7045 (Packard-Bell) | |
| 04f2:b071 | CNF7129 (Asus N10JA2, EeePC 1000HE, K50IN) | [3][14] |
| 04f2:b073 | CNF7231 (MSI MS-1722 ID1) | |
| 04f2:b082 | CKA7227 (HP EliteBook 2530p) | |
| 04f2:b083 | CKF7063 (HP Compaq 6830s) | |
| 04f2:b105 | Lenovo EasyCamera (IdeaPad Y530) | |
| 04f2:b106 | CNF7246 (Asus G71V) | |
| 04f2:b107 | CNF7070 (HP 2133) | |
| 04f2:b169 | CNF8248 (Fujitsu Lifebook T731) | [3] |
| 04f2:b221 | Integrated Camera (Lenovo Thinkpad T420s) | |
| 04f2:b230 | HP HD Webcam [Fixed] | [3] |

### OmniVision
| USB ID | Model | Notlar |
|--------|-------|--------|
| 05a9:2640 | OmniVision OV2640 (Dell Inspiron 1420/1720) | |
| 05a9:2643 | OmniVision Monitor Webcam (Dell SP2208WFP) | |
| 05a9:2649 | OmniVision Monitor Webcam (Dell SP2309W) | |
| 05a9:264b | Dell Studio Hybrid 140g | |
| 05a9:7670 | OmniVision OV7670 (Dell XPS m1330) | |

### Apple
| USB ID | Model | Notlar |
|--------|-------|--------|
| 05ac:8502 | Apple built-in iSight | [4] |

### Diğer Markalar

| USB ID | Model | Üretici | Notlar |
|--------|-------|---------|--------|
| 05c8:0103 | FO13FF-65 PC-CAM | Foxlink | |
| 05c8:0403 | HP Webcam [2 MP Fixed] (HP Mini 5103) | Foxlink | |
| 05ca:181c | Laptop Integrated Webcam FHD (Dell Latitude E6520) | Ricoh | |
| 05ca:18a1 | Integrated Webcam (Dell Studio 1535) | Ricoh | |
| 05ca:18b7 | Sony Visual Communication Camera (Sony VPCS12J1E) | Ricoh | |
| 05e3:0505 | BW Microscope | GenesysLogic | |
| 064e:8100 | Integrated Webcam 2M (Dell Vostro 1088) | SuYin | |
| 064e:a100 | Acer OrbiCam | SuYin | |
| 064e:a101 | Acer CrystalEye webcam | SuYin | |
| 064e:a102 | Webcam (Acer Timeline 1810T) | SuYin | |
| 064e:a110 | HP Webcam (HP TX2000) | SuYin | |
| 064e:a116 | USB 2.0 UVC 1.3M WebCam (Asus N20A) | SuYin | [3] |
| 064e:a117 | Acer HD Crystal Eye webcam (Acer 4930) | SuYin | |
| 064e:a118 | Integrated Webcam (Dell Mini 9) | SuYin | |
| 064e:a219 | UVC 1.3M Webcam (Acer Aspire 5745G) | SuYin | |
| 06f8:3005 | Hercules Dualpix Exchange | Guillemot | |
| 06f8:3007 | Hercules Dualpix Chat and Show | Guillemot | |
| 06f8:300a | Hercules Dualpix Infinite | Guillemot | |
| 06f8:300c | Hercules Classic Silver | Guillemot | |
| 06f8:3017 | Hercules HD Sunset | Guillemot | |
| 06f8:301c | Hercules Optical Glass | Guillemot | |
| 06f8:3020 | Hercules Webcam EC300 | Guillemot | |
| 090c:37b3 | Lenovo EasyCamera (Lenovo G560) | Silicon Motion | |
| 090c:b370 | Silicon Motion SM370 | Silicon Motion | |
| 090c:b371 | Silicon Motion SM371 | Silicon Motion | |
| 093a:2700 | iSonic W002 / A4Tech PK-635K / Digital Innovations 1.3MP | Pixart Imaging | |
| 093a:2800 | DealExtreme USB 2.0 Camera | Pixart Imaging | |
| 093a:2900 | Agama V-315 | Pixart Imaging | |
| 0ac8:0336 | Elecom UCAM-DLQ30 (Vimicro VC0336 chipset) | Solid Years | |
| 0ac8:332d | Vega USB 2.0 Camera (AOC / Techsolo TCA-4900) | Vimicro | |
| 0ac8:3410 | Venus USB 2.0 Camera (Minoru3D) | Vimicro | [8] |
| 0ac8:3420 | Venus USB 2.0 Camera (Tevion MD 85872 / Minoru3D) | Vimicro | [8] |
| 0ac8:3450 | A4Tech PK-333E | A4Tech | |
| 0ac8:3460 | Kodak Dual Webcamera | Sakar Corp. | |
| 0ac8:3610 | VMS-004D - 400x USB Microscope | Veho | [11] |
| 0ac8:c302 | Vega USB 2.0 Camera (Samsung Q45) | Vimicro | |
| 0ac8:c303 | Saturn USB 2.0 Camera (Samsung screens) | Vimicro | |
| 0ac8:c315 | HP Elite Autofocus Webcam | Vimicro | |
| 0ac8:c338 | Namuge 2MP Webcam | Namuga | |
| 0bda:56ff | Rear Camera (Sony Vaio SVF13N1L2E) | Realtek | |
| 0bda:5801 | Realtek 2SF022 (HP Pavillon DV7 4151SG) | Realtek | |
| 0c45:62c0 | Sonix USB 2.0 Camera / Trust SpotLight Pro / Centrios 1.3MP | Sonix | |
| 0c45:62e0 | MSI Starcam Racer / Rosewill RCM-8163 | Sonix | |
| 0c45:62f1 | Avatec CMA-L688 / HueHD | Sonix | [11] |
| 0c45:6310 | USB 2.0 Camera (Trust Chat Webcam) | Sonix | |
| 0c45:63e0 | Sonix Integrated Webcam (Dell) | Sonix | |
| 0c45:63ea | Laptop Integrated Webcam 2M (Dell Studio 1555) | Sonix | |
| 0c45:6409 | USB 2.0 Camera (Nokia Booklet 3G) | Sonix | |
| 0c45:6415 | Laptop Integrated Webcam 1.3M (Dell Inspiron 13z) | Sonix | |
| 13d3:509b | USB 2.0 Camera (Asus EeePC T91) | Genesys Logic | |
| 13d3:5103 | USB 2.0 Camera (Medion Akoya AIO) | Sonix | |
| 13d3:5122 | USB 2.0 Camera (Asus NX90Jq ve U33JC) | Sonix | [3] |
| 13d3:5130 | USB 2.0 Camera (Asus K40AE, K50IE, K52JT) | Sonix | [3] |
| 13d3:5702 | USB 2.0 UVC VGA WebCam (Asus Eee PC 1001PXD) | Azurewave | |
| 13d3:5710 | USB 2.0 UVC VGA WebCam (Asus U31SD) | Azurewave | |
| 13d3:5711 | USB 2.0 UVC VGA WebCam (Asus EeePC 1015PX) | Azurewave | |
| 145f:013e | Trust Megapixel USB2 WB-5600R | Trust | |
| 145f:013f | Trust Megapixel USB2 Auto Focus Webcam | Trust | |
| 145f:0142 | Trust WB-6250X Webcam | Trust | |
| 145f:015b | Trust WB-8500X Webcam | Trust | |
| 152d:0310 | JMicron USB2.0 XGA WebCam | JMicron | |
| 174f:1118 | Syntek D-Max HP Webcam (HP DV3) | Syntek | |
| 174f:5212 | Syntek USB 2.0 UVC PC Camera (HP Spartan) | Syntek | |
| 174f:5271 | Syntek USB 2.0 UVC PC Camera | Syntek | |
| 174f:5931 | Syntek USB 2.0 UVC PC Camera (Samsung Q310) | Syntek | |
| 174f:8a12 | Syntek USB 2.0 UVC PC Camera (Packard Bell MX52) | Syntek | |
| 174f:8a33 | Syntek USB 2.0 UVC PC Camera (Asus U3S) | Syntek | |
| 17ef:1004 | Integrated Camera (Lenovo Thinkpad T61) | Lenovo | |
| 17ef:480b | Integrated Camera (Lenovo SL400/SL500) | Lenovo | |
| 17ef:481c | Integrated Camera (Lenovo SL510) | Lenovo | |
| 1bcf:2809 | Laptop Integrated Webcam FHD (Dell Vostro 3550) | Sunplus | |
| 1c4f:3000 | SiGma Micro USB Web Camera | SiGma Micro | |
| 1e4e:0100 | USB 2.0 Camera | Etron Technologies | [10] |
| 1e4e:0102 | USB 2.0 Camera | Etron Technologies | |
| 2935:0001 | Magewell XI100DUSB-HDMI | Magewell | |
| 5986:0100 | Acer OrbiCam | Bison Electronics | |
| 5986:0101 | USB2.0 Camera (Packard Bell Easynote SJ) | Bison Electronics | |
| 5986:0102 | Acer Crystal Eye webcam (TravelMate 7720) | Bison Electronics | |
| 5986:0200 | Acer OrbiCam | Bison Electronics | |
| 5986:0202 | Bison (Fujitsu-Siemens Amilo SI2636) | Bison Electronics | |
| 5986:0203 | Bison (Advent 4211 ve MSI Wind) | Bison Electronics | |
| 5986:0205 | Lenovo EasyCamera (N500 ve U330) | Bison Electronics | [9] |
| 5986:0241 | Bison (MSI Wind Top AE1900) | Bison Electronics | [15] |
| 5986:0314 | BisonCam, NB Pro (MSI Wind U135DX) | Bison Electronics | |
| 5986:0343 | BisonCam, NB Pro (Clevo P150HM) | Bison Electronics | |
| eb1a:2571 | eMPIA 27xx based camera (unbranded) | eMPIA Technology | |
| eb1a:2761 | eMPIA 2761 based camera (unbranded) | eMPIA Technology | |
| eb1a:2771 | eMPIA 2771 based camera (Intelbras iPlug) | eMPIA Technology | |
| eb1a:299f | Supereyes Borescope | eMPIA Technology | |

---

## 🔧 Kameranın Algılanıp Algılanmadığını Test Etme

```bash
# Bağlı UVC cihazlarını listele
lsusb

# Video cihazlarını göster
ls /dev/video*

# Kamera bilgisini sorgula
v4l2-ctl --list-devices

# Görüntü testi (ffmpeg ile)
ffplay /dev/video0
```

---

## 📌 Kullanılan Driver

Bu kameralar Linux kernel'indeki **`uvcvideo`** driver'ı ile çalışır.  
Kernel 2.6.26+ sürümlerinde varsayılan olarak dahilidir, ekstra kurulum gerekmez.

```bash
# Driver'ın yüklü olup olmadığını kontrol et
lsmod | grep uvcvideo

# Yüklü değilse
sudo modprobe uvcvideo
```
