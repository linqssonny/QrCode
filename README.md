#使用方式
    api 'com.sonnyjack.library:qrcode:0.1.0'  或者
    api 'com.sonnyjack.library:qrcode:0.1.0'
    
该库引用com.android.support:appcompat-v7:27.1.0，如果你想统一你项目中的appcompat-v7的版本，可像这样引用：

       api ('com.sonnyjack.library:qrcode:0.1.0'){
            exclude(group: 'com.android.support', module: 'appcompat-v7')
        }

如果你的项目混淆：

-dontwarn com.sonnyjack.library.**

-keep class com.sonnyjack.library.** {*;}

一、扫描二维码、条形码用法：

        //扫描二维码/条形码
        startActivityForResult(new Intent(getActivity(), CaptureActivity.class), REQUESTCODE);

   然后在所在的activity的onActivityResult方法接收扫描返回值：

        @Override
        protected void onActivityResult(int requestCode, int resultCode, Intent data) {
            super.onActivityResult(requestCode, resultCode, data);
            if (RESULT_OK == resultCode) {
                 switch (requestCode) {
                    case REQUESTCODE:
                         String result = data.getStringExtra(CaptureActivity.QR_CODE_RESULT);
                         //what you want to do
                    break;
                 }
            }
        }
        

二、生成二维码用法：

        Bitmap bitmap = QrCodeUtils.buildQrCodeBitmap(value, size, size);
        //如果你想中间带上logo(Bitmap)，可使用下面方法
        Bitmap bitmap = QrCodeUtils.buildQrCodeBitmap(value, size, size, logo);
三、生成条形码：

        Bitmap bitmap = QrCodeUtils.buildBarCodeBitmap(value, width, height);
四、读取二维码、条形码

        //二维码
        String s = QrCodeUtils.decodeQrCode(bitmap);
        //条形码
        String s = QrCodeUtils.decodeBarCode(bitmap);

如果遇到什么问题可以加我Q：252624617  或者issues反馈