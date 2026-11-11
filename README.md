# vbmeta-for-galaxy-sm-a135f-dsn
This is a vbmeta img for the Samsung Galaxy SM-A135F/DSN.

## Where does this work? ##
It is important that you know this vbmeta image has been tested only on the DSN variant of the Samsung Galaxy A135F and that your bootloader revision must be equal to 0xd. Any other binary or device is not guaranteed to work with this vbmeta.

## Important Note ##
Important note: I was helped by AI because I am not a professional, sorry.

## How was the vbmeta file created ##
This vbmeta image was create to solve a personal issue with the Samsung Galaxy SM-A135F/DSN. When flashing a vbmeta image, I always got the Anti-Rollback feature activated and so Download Mode told me: SW REV CHECK FAIL: DEVICE(vbmeta) BINARY 0xd > 0x0. 

So I started using avbtool to create valid vbmeta images with the rollback index set to 13, but that seemed not to work, I was getting the same error.

To solve the issue, I tried generating a test image with the avbtool argument "generate_test_image" and tried to flash it. That got me past the Anti-Rollback feature, but the phone refused to boot because vbmeta did not have a valid header. 

So I generated a 256 Bytes valid vbmeta image using the avbtool function "make_vbmeta_image", with the rollback index set to 13, then I generated a 4Kb test vbmeta image with "generate_test_image".

Finally, I use dd to overwrite the first 256 Bytes of the test vbmeta with the valid vbmeta and that made the phone boot TWRP.
