---
title: Скачивание и установка sqlpackage | Документация Майкрософт
description: Скачивание и установка sqlpackage для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
ms.openlocfilehash: f966de4951e5c90dac8d6e48f00f8de6ff067e3c
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73033013"
---
# <a name="download-and-install-sqlpackage"></a>Скачивание и установка sqlpackage

Программа sqlpackage выполняется в Windows, macOS и Linux.

Скачайте и установите последний выпуск платформы .NET Framework, а также предварительные версии для macOS и Linux:

|Платформа|Загрузить|Дата выпуска|Версия|Сборка
|:---|:---|:---|:---|:---|
|Windows (x64)|[Установщик MSI](https://go.microsoft.com/fwlink/?linkid=2108813)|29 октября 2019 г.|18.4|15.0.4573.2|
|macOS .NET Core (x64)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2108815)|29 октября 2019 г.| 18.4|15.0.4573.2|
|Linux .NET Core (x64) |[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2108814)|29 октября 2019 г.| 18.4|15.0.4573.2|
|Windows .NET Core (x64) |[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2109019)|29 октября 2019 г.| 18.4|15.0.4573.2|

Подробнее см. в [заметках о выпуске](release-notes-sqlpackage.md). Чтобы скачать дополнительные языки, ознакомьтесь с разделом [Доступные языки](#available-languages) .

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Получение sqlpackage для Windows

Этот выпуск sqlpackage включает стандартные средства установщика Windows и ZIP-файл: 

1. Скачайте и запустите [установщик DacFramework.msi для Windows](https://go.microsoft.com/fwlink/?linkid=2108813).
2. Откройте новое окно командной строки и запустите файл sqlpackage.exe.
    - Программа sqlpackage устанавливается в папку ```C:\Program Files\Microsoft SQL Server\150\DAC\bin```.

## <a name="get-sqlpackage-net-core-for-windows"></a>Получение SqlPackage .NET Core для Windows

1. Скачайте [sqlpackage для Windows](https://go.microsoft.com/fwlink/?linkid=2109019).
2. Чтобы извлечь файл, щелкните правой кнопкой мыши файл в проводнике Windows и выберите пункт "извлечь все..." и укажите целевой каталог.
3. Откройте новое окно терминала и компакт-диск в папку, в которую был извлечен SqlPackage:

   ```cmd
   > sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-macos"></a>Получение SqlPackage .NET Core для macOS

1. Скачайте [sqlpackage для macOS](https://go.microsoft.com/fwlink/?linkid=2108815).
2. Чтобы извлечь файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   ```bash
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   $ echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   $ source ~/.bash_profile
   $ sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-linux"></a>Получение SqlPackage .NET Core для Linux

1. Скачайте [sqlpackage для Linux](https://go.microsoft.com/fwlink/?linkid=2108814) с помощью одного из установщиков или архива tar.gz:
2. Чтобы извлечь файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   ```bash
   cd ~
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   $ echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   $ chmod a+x ~/sqlpackage/sqlpackage
   $ source ~/.bashrc
   $ sqlpackage
   ```

   > [!NOTE]
   > В Debian, Redhat и Ubuntu, возможно, будут отсутствовать некоторые зависимости. Чтобы установить эти зависимости с учетом вашей версии Linux, используйте следующие команды:

   **Debian:**

   ```bash
   $ sudo apt-get install libunwind8
   ```

   **Redhat:**

   ```bash
   $ yum install libunwind
   $ yum install libicu
   ```

   **Ubuntu:**

   ```bash
   $ sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   $ sudo apt-get install libicu52      # for 14.x
   $ sudo apt-get install libicu55      # for 16.x
   $ sudo apt-get install libicu57      # for 17.x
   $ sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>Удаление sqlpackage (предварительная версия)

Если вы установили sqlpackage с помощью установщика Windows, удаление выполняется так же, как и для любого приложения Windows.

Если вы установили sqlpackage с помощью ZIP-файла или другого архива, удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Программа sqlpackage выполняется в Windows, macOS и Linux, а также поддерживается на следующих платформах:

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 7 с пакетом обновления 1 (SP1)
- Windows Server 2008 R2
- Windows Server 2012 R2
- Windows Server 2016

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="available-languages"></a>Доступные языки

Этот выпуск sqlpackage можно установить для следующих языков:

SqlPackage Windows:  
[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40a)

SqlPackage .NET Core Windows:  
[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40a)

SqlPackage .NET Core macOS:  
[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40a)

SqlPackage .NET Core Linux:  
[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40a)

## <a name="next-steps"></a>Next Steps

- См. подробнее о [sqlpackage](sqlpackage.md)

[Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
