---
title: Загрузите и установите sqlpackage | Документы Microsoft
description: Загрузка и установка sqlpackage для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 4e5528ca046de83385171890fbda389928e41cf3
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703851"
---
# <a name="download-and-install-sqlpackage"></a>Загрузите и установите sqlpackage

sqlpackage выполняется в Windows, macOS и Linux.

Загрузить и установить последний выпуск .NET Framework и macOS и предварительных версий Linux:

|Платформа|Загрузить|Дата выпуска|Версия|Сборка|
|:---|:---|:---|:---|:---|
|Windows|[Установщик](https://go.microsoft.com/fwlink/?linkid=875508)|25 января 2018|17.4.1|14.0.3917.1|
|macOS (Предварительная версия)|[ZIP](https://go.microsoft.com/fwlink/?linkid=873927)|9 мая 2018 г. |0.0.1|15.0.4057.1|
|Linux (предварительная версия)|[ZIP](https://go.microsoft.com/fwlink/?linkid=873926)|9 мая 2018 г. |0.0.1|15.0.4057.1|

## <a name="get-sqlpackage-for-windows"></a>Получение sqlpackage Windows

Этот выпуск sqlpackage включает стандартные возможности установщика Windows и .zip: 

**Установщик**

1. Загрузите и запустите [DacFramework.msi установщик Windows](https://go.microsoft.com/fwlink/?linkid=875508).
2. Откройте новое окно командной строки и выполните sqlpackage.exe
    - sqlpackage устанавливается в ```C:\Program Files\Microsoft SQL Server\140\DAC\bin``` папки

## <a name="get-sqlpackage-preview-for-macos"></a>Получить для macOS sqlpackage (Предварительная версия)

1. Загрузить [sqlpackage для macOS](https://go.microsoft.com/fwlink/?linkid=873927).
2. Извлеките файл и запустить sqlpackage, откройте новое окно терминала и введите следующие команды:

   **Установка ZIP:**
   ```bash 
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage 
   ``` 

## <a name="get-sqlpackage-preview-for-linux"></a>Получить sqlpackage (Предварительная версия) для Linux

1. Загрузить [sqlpackage для Linux](https://go.microsoft.com/fwlink/?linkid=873926) с помощью одного из установщиков или tar.gz архива:
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
   > В Debian, Redhat и Ubuntu могут быть потеряны зависимости. Используйте следующие команды для установки этих зависимостей в зависимости от вашей версии Linux:
   

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

Если вы установили sqlpackage с помощью установщика Windows, затем удалите так же, как удалить любое другое приложение Windows.

Если вы установили sqlpackage с расширением ZIP или других архива, просто удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

sqlpackage выполняется в Windows, macOS и Linux, а также поддерживается на следующих платформах:

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
- macOS 10.13 Сьерра высокого уровня
- macOS 10.12 Сьерра

### <a name="linux-x64"></a>Linux (x64)
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- Дополнительные сведения о [sqlpackage](sqlpackage.md)

[Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)
