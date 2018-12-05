---
title: Скачайте и установите sqlpackage | Документация Майкрософт
description: Скачайте и установите sqlpackage для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: e6585c78b26199c7ae5194e37d152db91aab1224
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52396320"
---
# <a name="download-and-install-sqlpackage"></a>Скачайте и установите sqlpackage

sqlpackage выполняется в Windows, macOS и Linux.

Скачайте и установите последний выпуск платформы .NET Framework и macOS и Linux предварительные версии:

|Платформа|Загрузить|Дата выпуска|Версия|Сборка
|:---|:---|:---|:---|:---|
|Windows|[Установщик MSI](https://go.microsoft.com/fwlink/?linkid=2033947)|24 октября 2018 г.|18.0|15.0.4200.1|
|macOS .NET Core (Предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2044514)|15 ноября 2018 г. | - |15.0.4240.1|
|Linux .NET Core (Предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2044263)|15 ноября 2018 г. | - |15.0.4240.1|

Дополнительные сведения о последнем выпуске см. в разделе [заметки о выпуске](sqlpackage-release-notes.md).

## <a name="get-sqlpackage-for-windows"></a>Получить sqlpackage для Windows

Этот выпуск sqlpackage включает стандартные возможности установщика Windows и ZIP-файл: 

1. Скачайте и запустите [DacFramework.msi установщик Windows](https://go.microsoft.com/fwlink/?linkid=2033947).
2. Откройте новое окно командной строки и запустите sqlpackage.exe
    - sqlpackage устанавливается в ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` папки
    - Установка x86 версии в x64 компьютере устанавливается sqlpackage ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin``` папки

## <a name="get-sqlpackage-preview-for-macos"></a>Получить sqlpackage (Предварительная версия) для macOS

1. Скачайте [sqlpackage для macOS](https://go.microsoft.com/fwlink/?linkid=2044514).
2. Извлеките файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   **Установка ZIP:**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Получить sqlpackage (Предварительная версия) для Linux

1. Скачайте [sqlpackage для Linux](https://go.microsoft.com/fwlink/?linkid=2044263) с помощью одного из установщиков или архива tar.gz:
2. Извлеките файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   **Установка ZIP:**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bashrc
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > В Debian, Redhat и Ubuntu возможно, отсутствуют зависимости. Чтобы установить эти зависимости, в зависимости от вашей версии Linux, используйте следующие команды:

   **Debian:**

   ```bash
   sudo apt-get install libuwind8
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

## <a name="uninstall-sqlpackage-preview"></a>Удалить sqlpackage (Предварительная версия)

Если вы установили sqlpackage, с помощью установщика Windows, затем удалите так же, как удалить любое приложение Windows.

Если вы установили sqlpackage с ZIP-файл или других архива, просто удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

sqlpackage работает в Windows, macOS и Linux и поддерживается на следующих платформах:

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

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- Дополнительные сведения о [sqlpackage](sqlpackage.md)

[Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
