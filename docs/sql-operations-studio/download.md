---
title: Загрузите и установите Microsoft SQL Operations Studio (Предварительная версия) | Документы Microsoft
description: Загрузка и установка Microsoft SQL Operations Studio (Предварительная версия) для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 05/08/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dcf6f9d14efd903c47d4e3b059503fb77606209b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Загрузите и установите SQL Operations Studio (Предварительная версия)

[!INCLUDE[name-sos](../includes/name-sos.md)] выполняется на Windows, macOS и Linux.

Загрузить и установить последний выпуск *может общедоступной предварительной версии*:

|Платформа|Загрузить|Дата выпуска| Версия |
|:---|:---|:---|:---|
|Windows|[Установщик](https://go.microsoft.com/fwlink/?linkid=873386)<br>[.ZIP](https://go.microsoft.com/fwlink/?linkid=873387)|7 мая 2018 |0.29.3|
|MacOS|[.ZIP](https://go.microsoft.com/fwlink/?linkid=873388)|7 мая 2018 |0.29.3|
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=873391)<br>[.RPM](https://go.microsoft.com/fwlink/?linkid=873390)<br>[. tar.gz](https://go.microsoft.com/fwlink/?linkid=873389)|7 мая 2018 |0.29.3|

Дополнительные сведения о последнем выпуске см. в разделе [заметки о выпуске](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Получение SQL Operations Studio (Предварительная версия) для Windows

Этот выпуск [!INCLUDE[name-sos](../includes/name-sos-short.md)] включает стандартные возможности установщика Windows и .zip: 

**Установщик**

1. Загрузите и запустите [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] установщик Windows](https://go.microsoft.com/fwlink/?linkid=873386).
1. Запуск [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] приложения.


**ZIP-файл**

1. Загрузить [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] .zip для Windows](https://go.microsoft.com/fwlink/?linkid=873387).
2. Найдите загруженный файл и извлеките его.
3. Выполнить `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Получить для macOS SQL Operations Studio (Предварительная версия)

1. Загрузить [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] для macOS](https://go.microsoft.com/fwlink/?linkid=873388).
2. Чтобы развернуть содержимое ZIP-файл, дважды щелкните его.
3. Чтобы сделать [!INCLUDE[name-sos](../includes/name-sos-short.md)] в *запуска*, перетащите *sqlops.app* для *приложений* папки.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Получить SQL Operations Studio (Предварительная версия) для Linux

1. Загрузить [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Linux с помощью одного из установщиков или tar.gz архива:
    - [.DEB](https://go.microsoft.com/fwlink/?linkid=873391)
    - [.RPM](https://go.microsoft.com/fwlink/?linkid=873390)
    - [. tar.gz](https://go.microsoft.com/fwlink/?linkid=873389)
1. Чтобы извлечь файл и запустите [!INCLUDE[name-sos](../includes/name-sos-short.md)], откройте новое окно терминала и введите следующие команды:

   **Debian установки:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **RPM установки:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **tar.gz установки:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > В Debian, Redhat и Ubuntu могут быть потеряны зависимости. Используйте следующие команды для установки этих зависимостей в зависимости от вашей версии Linux:
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **RedHat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>Удаление SQL Operations Studio (Предварительная версия)

Если вы установили [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] с помощью установщика Windows, удалите так же, как удалить любое другое приложение Windows.

Если вы установили [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] с расширением ZIP или других архива, просто удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

[!INCLUDE[name-sos](../includes/name-sos-short.md)] выполняется на Windows, Linux и macOS и поддерживается на следующих платформах:

### <a name="windows"></a>Windows
- Windows 10 (64-разрядная)
- Windows 8.1 (64-разрядная)
- Windows 8 (64-разрядная)
- Требуется Windows 7 (SP1) (64-разрядная версия) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

### <a name="macos"></a>MacOS
- macOS 10.13 Сьерра высокого уровня
- macOS 10.12 Сьерра

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Проверка обновлений
Чтобы проверить наличие последних обновлений, щелкните значок шестеренки в левом нижнем углу окна и нажмите кнопку **проверять наличие обновлений**

## <a name="next-steps"></a>Следующие шаги

См. один из следующих краткие руководства, чтобы приступить к работе:
- [Подключиться & запрос SQL Server](quickstart-sql-server.md)
- [Подключиться & запроса базы данных Azure SQL](quickstart-sql-database.md)
- [Подключиться & запроса хранилища данных Azure](quickstart-sql-dw.md)

Участие в [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Заявление о конфиденциальности Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) и [сбора данных об использовании](usage-data-collection.md).
