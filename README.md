# Настройка VPN VTB в Ubuntu

## Установка pcsc*

Проверить, что система видит токен: pcsc_scan
![pcsc_scan](https://user-images.githubusercontent.com/77896951/141649025-d9e0bcdf-c270-4438-ba73-6bdf83bc55fd.png)

Если система не видит токен, необходимо установить:
`sudo apt install pcscd pcsc-tools`

По необходимости стартовать pcscd

## Установка Safenet Authentication Client
Потребуется установить libssl1.1_1.1.1l-1ubuntu1.2_amd64.deb. 

Safenet найдите в сети и установите deb-пакет.

## Настройка Firefox

Скачайте VTB-сертификаты.

В браузере Firefox перейти в настройки управления шифрованием:
[Menu] Edit->[Menu] Preferences->[Tab] Advanced->[Tab] Certifivates

Открыть настройки управления сертификатами нажав кнопку View Certificates. В разделе Authorities поочередно импортировать все скачанные сертификаты.

Открыть настройки управления крипто-устройствами нажав кнопку Security Devices. Если в правой части списка не появился пункт с токеном, его нужно добавить вручную, нажав кнопку Load, задав имя для устройства и путь к модулю pkcs11:
`/usr/lib/libeTPkcs11.so`
Проблема: Firefox, как snap-пакет не видит устройство, нужно установить не snap-версию.

![sec_device](https://user-images.githubusercontent.com/77896951/141650184-385ec9a1-cf28-470d-8315-652028b791f4.png)


## Установка SFX:

[Смотри Linux setup Check Point Mobile Access VPN](https://github.com/pedroeml/checkpoint-mobile-access-vpn#linux-setup-check-point-mobile-access-vpn "Смотри Linux setup Check Point Mobile Access VPN")

Если в процессу установки cshell_install.sh ошибка:
`Cannot delete certificates. Installation aborted.`
может помочь переустановка firefox с повторным добавление сертификатов.

## Установка Сitrix-receiver

Устанавливаем citrix workspace app.

Если в процессе подключения возникает ошибка либо аналогичная (SSL):

![citrix_rec_error](https://user-images.githubusercontent.com/77896951/141650675-dbecba86-171a-4534-abb6-e9903ee557f1.png)

необходимо сертификат "VTB Group Root CA.cer" *.cer сконвертировать в *.pem и скопировать его в папку /opt/Citrix/ICAClient/keystore/cacerts/

`sudo cp "VTB Group Root CA.crt" /opt/Citrix/ICAClient/keystore/cacerts/`




