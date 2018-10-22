---
title: Скачайте и установите Studio данных Azure | Документация Майкрософт
description: Загрузка и установка Azure данных Studio для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07c5e65558bf4544da08f631a1d57290352bb451
ms.sourcegitcommit: ef115025e57ec342c14ed3151ce006f484d1fadc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2018
ms.locfileid: "49411141"
---
# <a name="download-and-install-azure-data-studio"></a>Скачайте и установите Studio данных Azure

[!INCLUDE[name-sos](../includes/name-sos.md)] выполняется в Windows, macOS и Linux.

Скачайте и установите последний выпуск *выпуска октября*:

> [!NOTE]
> Если вы выполняете обновление с SQL Operations Studio и хотите сохранить ваши параметры, сочетания клавиш или фрагменты кода, см. в разделе [перемещение параметров пользователя](#move-user-settings).

|Платформа|Загрузить|Дата выпуска| Версия |
|:---|:---|:---|:---|
|Windows|[Установщик](https://go.microsoft.com/fwlink/?linkid=2030731)<br>[ZIP](https://go.microsoft.com/fwlink/?linkid=2030736)|18 октября 2018 г. |1.1.3|
|macOS|[ZIP](https://go.microsoft.com/fwlink/?linkid=2030738)|18 октября 2018 г. |1.1.3|
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=2030750)<br>[.RPM](https://go.microsoft.com/fwlink/?linkid=2030746)<br>[. tar.gz](https://go.microsoft.com/fwlink/?linkid=2030741)|18 октября 2018 г. |1.1.3|

Дополнительные сведения о последнем выпуске см. в разделе [заметки о выпуске](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Получить Studio данных Azure для Windows

Этот выпуск [!INCLUDE[name-sos](../includes/name-sos-short.md)] включает в себя стандартные возможности установщика Windows и ZIP-файл: 

**Установщик**

1. Скачайте и запустите [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] установщик Windows](https://go.microsoft.com/fwlink/?linkid=2030731).
1. Запуск [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] приложения.


**ZIP-файл**

1. Скачайте [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP-файл для Windows](https://go.microsoft.com/fwlink/?linkid=2030736).
2. Найдите скачанный файл и извлеките его содержимое.
3. Выполнить `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Получение данных в студии для macOS

1. Скачайте [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] для macOS](https://go.microsoft.com/fwlink/?linkid=2030738).
2. Чтобы развернуть содержимое ZIP-файл, дважды щелкните его.
3. Чтобы сделать [!INCLUDE[name-sos](../includes/name-sos-short.md)] в *панель запуска*, перетащите *Studio.app данных Azure* для *приложений* папки.


## <a name="get-azure-data-studio-for-linux"></a>Получить Studio данных Azure для Linux

1. Скачайте [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Linux с помощью одного из установщиков или архива tar.gz:
    - [.DEB](https://go.microsoft.com/fwlink/?linkid=2030750)
    - [.RPM](https://go.microsoft.com/fwlink/?linkid=2030746)
    - [. tar.gz](https://go.microsoft.com/fwlink/?linkid=2030741)
1. Чтобы извлечь файл и запустить [!INCLUDE[name-sos](../includes/name-sos-short.md)], откройте новое окно терминала и введите следующие команды:

   **Установка на Debian:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **RPM установки:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **tar.gz установки:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > В Debian, Redhat и Ubuntu возможно, отсутствуют зависимости. Чтобы установить эти зависимости, в зависимости от вашей версии Linux, используйте следующие команды:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
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


## <a name="uninstall-azure-data-studio"></a>Удаление Studio данных Azure

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

## <a name="supported-sql-offerings-ssms-180-preview"></a>Поддерживаемые предложения SQL (Предварительная версия SSMS 18.0)

* Эта версия Azure Data Studio работает со всеми [поддерживаемых версиях SQL Server 2014 - [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) и обеспечивает поддержку для работы с новейшими облачными функциями в базе данных SQL Azure и хранилище данных SQL Azure. Azure Data Studio также предоставляет поддержку предварительной версии управляемого экземпляра SQL Azure.

## <a name="move-user-settings"></a>Перемещение параметров пользователя

Если вы хотите переместить ваши пользовательские настройки, сочетания клавиш или фрагменты кода, выполните следующие действия. Это важно в случае, если вы обновляете версию SQL Operations Studio студию данных Azure.

*Если у вас уже есть Azure Data Studio, или вы никогда не установлены или настроены SQL Operations Studio, можно игнорировать в этом разделе.*


1. Откройте параметры, щелкните значок шестеренки в левом нижнем углу и выберите **параметры.**

   ![открыть параметры](./media/download/open-settings.png)

2. Щелкните правой кнопкой мыши **параметры пользователя** вкладке в верхней части и нажмите кнопку **отобразить в проводнике**

   ![Показать в обозревателе](./media/download/reveal-in-explorer.png)

3. Скопируйте все файлы в этой папке и сохраните в удобном для поиска расположения на локальном диске, такие как папки «документы».

   ![Параметры копирования](./media/download/copy-settings.png)

4. В вашей новой версии Azure Data Studio выполните шаги 1-2, затем для шага 3 вставить содержимое, сохраненный в папке. Можно также вручную скопировать параметры, сочетания клавиш или фрагменты в своих подразделениях.


## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с одним из следующих кратких руководств, чтобы приступить к работе:
- [Подключение и отправка запроса SQL Server](quickstart-sql-server.md)
- [Подключение и отправка запроса база данных Azure SQL](quickstart-sql-database.md)
- [Подключение и запросы к хранилищу данных Azure](quickstart-sql-dw.md)

Участие в разработке [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Заявление о конфиденциальности Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) и [сбора данных об использовании](usage-data-collection.md).
