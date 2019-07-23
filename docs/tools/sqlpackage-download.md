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
ms.openlocfilehash: 406fb50ceaba177d02bf8d79d0c37191dbe178f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986252"
---
# <a name="download-and-install-sqlpackage"></a>Скачивание и установка sqlpackage

Программа sqlpackage выполняется в Windows, macOS и Linux.

Скачайте и установите последний выпуск платформы .NET Framework, а также предварительные версии для macOS и Linux:

|Платформа|Загрузить|Дата выпуска|Версия|Сборка
|:---|:---|:---|:---|:---|
|Windows|[Установщик MSI](https://go.microsoft.com/fwlink/?linkid=2087429)|15 апреля 2019 г.|18.2|15.0.4384.2|
|macOS .NET Core (предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2087247)|15 апреля 2019 г. | 18.2 |15.0.4384.2|
|Linux .NET Core (предварительная версия)|[ZIP-файл](https://go.microsoft.com/fwlink/?linkid=2087431)|15 апреля 2019 г. | 18.2 |15.0.4384.2|

Подробнее см. в [заметках о выпуске](release-notes-sqlpackage.md).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Получение sqlpackage для Windows

Этот выпуск sqlpackage включает стандартные средства установщика Windows и ZIP-файл: 

1. Скачайте и запустите [установщик DacFramework.msi для Windows](https://go.microsoft.com/fwlink/?linkid=2087429).
2. Откройте новое окно командной строки и запустите файл sqlpackage.exe.
    - Программа sqlpackage устанавливается в папку ```C:\Program Files\Microsoft SQL Server\150\DAC\bin```.
    - При установке версии x86 на x64-разрядном компьютере sqlpackage устанавливается в папку ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin```.

## <a name="get-sqlpackage-preview-for-macos"></a>Получение sqlpackage (предварительная версия) для macOS

1. Скачайте [sqlpackage для macOS](https://go.microsoft.com/fwlink/?linkid=2087247).
2. Чтобы извлечь файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   **Установка ZIP:**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Получение sqlpackage (предварительная версия) для Linux

1. Скачайте [sqlpackage для Linux](https://go.microsoft.com/fwlink/?linkid=2087431) с помощью одного из установщиков или архива tar.gz:
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
