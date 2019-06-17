---
title: Загрузите и установите
titleSuffix: Azure Data Studio
description: Загрузка и установка Azure данных Studio для Windows, macOS или Linux
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.custom: seodec18
ms.date: 06/06/2019
ms.reviewer: alayu; sstein
ms.openlocfilehash: b8de39cd3039c24420325dbff5ffb3f1db4efd40
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801852"
---
# <a name="download-and-install-azure-data-studio"></a>Скачайте и установите Studio данных Azure

[!INCLUDE[name-sos](../includes/name-sos.md)] выполняется в Windows, macOS и Linux.


Скачайте и установите последний выпуск *Июньский выпуск*:

> [!NOTE]
> Если вы выполняете обновление с SQL Operations Studio и хотите сохранить ваши параметры, сочетания клавиш или фрагменты кода, см. в разделе [перемещение параметров пользователя](#move-user-settings).

|Платформа|Загрузить|Дата выпуска| Версия |
|:---|:---|:---|:---|
|Windows|[Установщик для пользователя (рекомендуется)](https://go.microsoft.com/fwlink/?linkid=2094100)<br>[Установщик системы](https://go.microsoft.com/fwlink/?linkid=2094200)<br>[ZIP](https://go.microsoft.com/fwlink/?linkid=2094201)|6 июня 2019 г. |1.8.0|
|macOS|[ZIP](https://go.microsoft.com/fwlink/?linkid=2094202)|6 июня 2019 г. |1.8.0|
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=2094203)<br>[.RPM](https://go.microsoft.com/fwlink/?linkid=2094102)<br>[. tar.gz](https://go.microsoft.com/fwlink/?linkid=2094101)|6 июня 2019 г. |1.8.0|

Подробнее см. в [заметках о выпуске](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Получить Studio данных Azure для Windows

Этот выпуск [!INCLUDE[name-sos](../includes/name-sos-short.md)] включает в себя стандартные возможности установщика Windows и ZIP-файл.

*Установщик пользователя* рекомендуется, так как он не требуются права администратора, что упрощает установок и обновлений. Установщик для пользователя не требуются права администратора, что и расположение находится в папке AppData (LOCALAPPDATA) пользователя. Установщик для пользователя также предоставляет более стабильную работу фонового обновления. Дополнительные сведения см. в разделе [настройки пользователя для Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).


**Установщик для пользователя** (рекомендуется)

1. Скачайте и запустите [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *пользователя* установщик Windows](https://go.microsoft.com/fwlink/?linkid=2094100).
2. Запуск [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] приложения.

**Установщик системы**

1. Скачайте и запустите [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *системы* установщик Windows](https://go.microsoft.com/fwlink/?linkid=2094200).
2. Запуск [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] приложения.


**ZIP-файл**

1. Скачайте [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP-файл для Windows](https://go.microsoft.com/fwlink/?linkid=2094201).
2. Найдите скачанный файл и извлеките его содержимое.
3. Выполнить `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Получение данных в студии для macOS

1. Скачайте [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] для macOS](https://go.microsoft.com/fwlink/?linkid=2094202).
2. Чтобы развернуть содержимое ZIP-файл, дважды щелкните его.
3. Чтобы сделать [!INCLUDE[name-sos](../includes/name-sos-short.md)] в *панель запуска*, перетащите *Studio.app данных Azure* для *приложений* папки.


## <a name="get-azure-data-studio-for-linux"></a>Получить Studio данных Azure для Linux

1. Скачайте [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Linux с помощью одного из установщиков или архива tar.gz:
    - [.DEB](https://go.microsoft.com/fwlink/?linkid=2094203)
    - [.RPM](https://go.microsoft.com/fwlink/?linkid=2094102)
    - [. tar.gz](https://go.microsoft.com/fwlink/?linkid=2094101)
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
   > В Debian, Redhat и Ubuntu, возможно, будут отсутствовать некоторые зависимости. Чтобы установить эти зависимости с учетом вашей версии Linux, используйте следующие команды:
   

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
- Требуется Windows 7 (SP1) (64-разрядная версия) — [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>Рекомендуемые требования к системе
Для оптимальной производительности используйте рекомендованным системным требованиям.
[Требуется обновление здесь возможность измерить памяти]

|             | Число ядер ЦП | Памяти и оперативной памяти |
|:-----------|:---------|:----------|
| Рекомендуемая |     4     |      8 ГБ    |
|   Минимальные   |     2     |      4 ГБ     |
|             |           |            |

## <a name="check-for-updates"></a>Проверка обновлений
Чтобы проверить наличие последних обновлений, щелкните значок шестеренки в нижней левой части окна, а затем **проверять наличие обновлений**

## <a name="supported-sql-offerings"></a>Поддерживаемые предложения SQL

* Эта версия Azure Data Studio работает со всеми [поддерживаемых версиях SQL Server 2014 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ](https://support.microsoft.com/lifecycle?C2=1044) и обеспечивает поддержку для работы с новейшими облачными функциями в базе данных SQL Azure и хранилище данных SQL Azure. Azure Data Studio также предоставляет поддержку предварительной версии управляемого экземпляра SQL Azure.

## <a name="upgrade-from-sql-operations-studio"></a>Обновление с SQL Operations Studio

Если вы все еще используете SQL Operations Studio, необходимо обновить до студию данных Azure. SQL Operations Studio был имя Предварительная версия и предварительная версия Azure Data Studio. В сентябре 2018 года мы [имя изменено на Azure Data Studio](https://cloudblogs.microsoft.com/sqlserver/2018/09/25/azure-data-studio-for-sql-server/) и выпущенной версии общей доступности (GA). Так как SQL Operations Studio больше не обновлен или не поддерживается, мы просим всех пользователей SQL Operations Studio для загрузки последней версии Azure Data Studio, чтобы опробовать новейшие функции, обновления безопасности и исправления.
 
При обновлении старого предварительной версии до последней Studio данных Azure, вы потеряете текущих настроек и расширений. Чтобы переместить параметры, следуйте инструкциям в следующих *перемещение параметров пользователя* раздел:


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

5. Если переопределяет существующую установку, удалите старый каталог установки перед установкой, чтобы избежать ошибок при подключении к учетной записи Azure в обозревателе ресурсов.

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с одним из следующих кратких руководств, чтобы приступить к работе:
- [Подключение и отправка запроса SQL Server](quickstart-sql-server.md)
- [Подключение и отправка запроса база данных Azure SQL](quickstart-sql-database.md)
- [Подключение и запросы к хранилищу данных Azure](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Заявление о конфиденциальности Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) и [сбора данных об использовании](usage-data-collection.md).