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
ms.openlocfilehash: 01654df047d2dc78014c6e8c41edbb370d15da60
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874388"
---
# <a name="download-and-install-sqlpackage"></a>Скачивание и установка sqlpackage

Программа sqlpackage выполняется в Windows, macOS и Linux.

Скачайте и установите последний выпуск платформы .NET Framework, а также предварительные версии для macOS и Linux:

|Платформа|Загрузить|Дата выпуска|Версия|Сборка
|:---|:---|:---|:---|:---|
|Windows|[Установщик MSI](https://go.microsoft.com/fwlink/?linkid=2102893)|6 сентября 2019 г.|18,3|15.0.4532.1|
|macOS .NET Core (предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2102894)|6 сентября 2019 г.| 18,3|15.0.4532.1|
|Linux .NET Core (предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2102978)|6 сентября 2019 г.| 18,3|15.0.4532.1|
|Windows .NET Core (Предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2102979)|6 сентября 2019 г.| 18,3|15.0.4532.1|

Подробнее см. в [заметках о выпуске](release-notes-sqlpackage.md).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Получение sqlpackage для Windows

Этот выпуск sqlpackage включает стандартные средства установщика Windows и ZIP-файл: 

1. Скачайте и запустите [установщик DacFramework.msi для Windows](https://go.microsoft.com/fwlink/?linkid=2102893).
2. Откройте новое окно командной строки и запустите файл sqlpackage.exe.
    - Программа sqlpackage устанавливается в папку ```C:\Program Files\Microsoft SQL Server\150\DAC\bin```.
    - При установке версии x86 на x64-разрядном компьютере sqlpackage устанавливается в папку ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin```.

## <a name="get-sqlpackage-net-core-preview-for-windows"></a>Получение SqlPackage .NET Core (Предварительная версия) для Windows

1. Скачайте [sqlpackage для Windows](https://go.microsoft.com/fwlink/?linkid=2102979).
2. Чтобы извлечь файл, щелкните правой кнопкой мыши файл в проводнике Windows и выберите пункт "извлечь все..." и укажите целевой каталог.
3. Откройте новые окна терминала, а также компакт-диск в расположение, где SqlPackage был ексрактед:

   **Установка ZIP:**

   ```bash
   sqlpackage
   ```

## <a name="get-sqlpackage-net-core-preview-for-macos"></a>Получение SqlPackage .NET Core (Предварительная версия) для macOS

1. Скачайте [sqlpackage для macOS](https://go.microsoft.com/fwlink/?linkid=2102894).
2. Чтобы извлечь файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   **Установка ZIP:**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-net-core-preview-for-linux"></a>Получение SqlPackage .NET Core (Предварительная версия) для Linux

1. Скачайте [sqlpackage для Linux](https://go.microsoft.com/fwlink/?linkid=2102978) с помощью одного из установщиков или архива tar.gz:
2. Чтобы извлечь файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   **Установка ZIP:**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   chmod a+x ~/sqlpackage/sqlpackage
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > В Debian, Redhat и Ubuntu, возможно, будут отсутствовать некоторые зависимости. Чтобы установить эти зависимости с учетом вашей версии Linux, используйте следующие команды:

   **Debian:**

   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:**

   ```bash
   yum install libunwind
   yum install libicu
   ```

   **Ubuntu:**

   ```bash
   sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   sudo apt-get install libicu52      # for 14.x
   sudo apt-get install libicu55      # for 16.x
   sudo apt-get install libicu57      # for 17.x
   sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>Удаление sqlpackage (предварительная версия)

Если вы установили sqlpackage с помощью установщика Windows, удаление выполняется так же, как и для любого приложения Windows.

Если вы установили sqlpackage с помощью ZIP-файла или другого архива, просто удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Программа sqlpackage выполняется в Windows, macOS и Linux, а также поддерживается на следующих платформах:

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 с пакетом обновления 1 (SP1)
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- См. подробнее о [sqlpackage](sqlpackage.md)

[Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
