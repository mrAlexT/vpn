# Настройка VPN VTB

## Установка pcsc*

`sudo apt install pcsc-tools`

По необходимости: 
`sudo apt-get install libccid pcscd libpcsclite1`

Проверить, что система видит токен:
![pcsc_scan](https://user-images.githubusercontent.com/77896951/141649025-d9e0bcdf-c270-4438-ba73-6bdf83bc55fd.png)

Если токен система не видит, необходимо установить драйвер:
[ASEDrive Driver](https://www.aladdin-rd.ru/support/downloads/readers)


## Установка Safenet authentication client
Установить deb-пакет

## Настройка Firefox

Скачать сертификаты.
В браузере Firefox перейти в настройки управления шифрованием:
[Menu] Edit->[Menu] Preferences->[Tab] Advanced->[Tab] Certifivates
Открыть настройки управления сертификатами нажав кнопку View Certificates.
В разделе Authorities поочередно импортировать все скачанные сертификаты.

Открыть настройки управления крипто-устройствами нажав кнопку Security Devices. Если в правой части списка не появился пункт с е-токеном, его нужно добавить вручную, нажав кнопку Load, задав имя для устройства и путь к модулю pkcs11:
`/usr/lib/libeTPkcs11.so`
![sec_device](https://user-images.githubusercontent.com/77896951/141650184-385ec9a1-cf28-470d-8315-652028b791f4.png)


## Установка SFX:
[Смотри Linux setup Check Point Mobile Access VPN](https://github.com/pedroeml/checkpoint-mobile-access-vpn#linux-setup-check-point-mobile-access-vpn "Смотри Linux setup Check Point Mobile Access VPN")

Если в процессу установки cshell_install.sh ошибка:
`Cannot delete certificates. Installation aborted.`
может помочь переустановка firefox с повторным добавление сертификатов.

## Установка Сitrix-receiver
[Устанавливаем](https://www.citrix.com/ru-ru/downloads/citrix-receiver/linux/) deb-пакет

Если в процессе подключения возникает ошибка:

![citrix_rec_error](https://user-images.githubusercontent.com/77896951/141650675-dbecba86-171a-4534-abb6-e9903ee557f1.png)

необходимо добавить сертификат
`sudo cp "VTB Group Root CA.crt" /opt/Citrix/ICAClient/keystore/cacerts/`




