---
title: Загрузите и установите Microsoft SQL Operations Studio (Предварительная версия) | Документы Microsoft
description: >
  Загрузка и установка Microsoft SQL Operations Studio (Предварительная версия) для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 07/19/2018
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
ms.openlocfilehash: 1cd69a0dbc2399c4b16a656d20731e4548739505
ms.sourcegitcommit: 4b21840f20195d70f255465666f7b409ba839d18
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39146824"
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Загрузите и установите SQL Operations Studio (Предварительная версия)

[!INCLUDE[name-sos](../includes/name-sos.md)] выполняется в Windows, macOS и Linux.

Скачайте и установите последний выпуск *общедоступной предварительной версии июля*:

|Платформа|Загрузить|Дата выпуска| Версия |
|:---|:---|:---|:---|
|Windows|[Установщик](https://go.microsoft.com/fwlink/?linkid=2005949)<br>[ZIP](https://go.microsoft.com/fwlink/?linkid=2005950)|19 июля 2018 г. |0.31.4|
|macOS|[ZIP](https://go.microsoft.com/fwlink/?linkid=2005959)|19 июля 2018 г. |0.31.4|
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=2006084)<br>[.RPM](https://go.microsoft.com/fwlink/?linkid=2006083)<br>[. tar.gz](https://go.microsoft.com/fwlink/?linkid=2005960)|19 июля 2018 г. |0.31.4|

Дополнительные сведения о последнем выпуске см. в разделе [заметки о выпуске](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Получение SQL Operations Studio (Предварительная версия) для Windows


Этот выпуск [!INCLUDE[name-sos](../includes/name-sos-short.md)] включает в себя стандартные возможности установщика Windows и ZIP-файл: 

**Установщик**

1. Скачайте и запустите [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] установщик Windows](https://go.microsoft.com/fwlink/?linkid=2005949).
1. Запуск [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] приложения.


**ZIP-файл**

1. Скачайте [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP-файл для Windows](https://go.microsoft.com/fwlink/?linkid=2005950).
2. Найдите скачанный файл и извлеките его содержимое.
3. Выполнить `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Получить для macOS SQL Operations Studio (Предварительная версия)

1. Скачайте [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] для macOS](https://go.microsoft.com/fwlink/?linkid=2005959).
2. Чтобы развернуть содержимое ZIP-файл, дважды щелкните его.
3. Чтобы сделать [!INCLUDE[name-sos](../includes/name-sos-short.md)] в *панель запуска*, перетащите *sqlops.app* для *приложений* папки.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Получить SQL Operations Studio (Предварительная версия) для Linux

1. Скачайте [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Linux с помощью одного из установщиков или архива tar.gz:
    - [.DEB](https://go.microsoft.com/fwlink/?linkid=2006084)
    - [.RPM](https://go.microsoft.com/fwlink/?linkid=2006083)
    - [. tar.gz](https://go.microsoft.com/fwlink/?linkid=2005960)
1. Чтобы извлечь файл и запустить [!INCLUDE[name-sos](../includes/name-sos-short.md)], откройте новое окно терминала и введите следующие команды:

   **Установка на Debian:**
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
   > В Debian, Redhat и Ubuntu возможно, отсутствуют зависимости. Чтобы установить эти зависимости, в зависимости от вашей версии Linux, используйте следующие команды:
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:** 
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


Если вы установили [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] с помощью установщика Windows, удалите это так же, как удалить любое приложение Windows.

Если вы установили [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] с ZIP-файл или других архива, просто удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

[!INCLUDE[name-sos](../includes/name-sos-short.md)] работает в Windows, macOS и Linux и поддерживается на следующих платформах:

### <a name="windows"></a>Windows
- Windows 10 (64-разрядная)
- Windows 8.1 (64-разрядная)
- Windows 8 (64-разрядная)
- Требуется Windows 7 (SP1) (64-разрядная версия) — [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="check-for-updates"></a>Проверка обновлений
Чтобы проверить наличие последних обновлений, щелкните значок шестеренки в нижней левой части окна, а затем **проверять наличие обновлений**

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с одним из следующих кратких руководств, чтобы приступить к работе:
- [Подключение и отправка запроса SQL Server](quickstart-sql-server.md)
- [Подключение и отправка запроса база данных Azure SQL](quickstart-sql-database.md)
- [Подключение и запросы к хранилищу данных Azure](quickstart-sql-dw.md)

Участие в разработке [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Заявление о конфиденциальности Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) и [сбора данных об использовании](usage-data-collection.md).
