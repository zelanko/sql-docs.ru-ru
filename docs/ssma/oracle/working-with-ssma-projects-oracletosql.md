---
title: Работа с проектами SSMA (OracleToSQL) | Документация Майкрософт
description: Узнайте, как создать проект SSMA, содержащий метаданные для баз данных Oracle, которые необходимо перенести и SQL Server, а также параметры и сведения о подключении.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Customizing Project Settings
ms.assetid: ee5d94c0-c7a6-4779-bd32-729bdaf61e1b
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 285665d1720b941523871d00fed9a0d2239c7d78
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84294041"
---
# <a name="working-with-ssma-projects-oracletosql"></a>Работа с проектами SSMA (OracleToSQL)
Чтобы перенести базы данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , сначала необходимо создать проект SSMA. Проект представляет собой файл, содержащий следующие сведения:  
  
-   Метаданные о базах данных Oracle, на которые необходимо выполнить миграцию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Метаданные о целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который будет принимать перенесенные объекты и данные.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]сведения о соединении.  
  
-   Параметры проекта.  
  
При открытии проекта он отключается от Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это позволяет работать в автономном режиме. Сведения о повторном подключении к см [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . в разделе [подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Просмотр параметров проекта по умолчанию  
SSMA содержит несколько параметров для преобразования и загрузки объектов базы данных, переноса данных и синхронизации SSMA с Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Параметры по умолчанию подходят для многих пользователей. Однако перед созданием нового проекта SSMA необходимо проверить параметры. При необходимости можно изменить параметры по умолчанию, которые будут использоваться для всех новых проектов.  
  
**Проверка параметров проекта по умолчанию**  
  
1.  В меню **Сервис** выберите пункт **Параметры проекта по умолчанию**.  
  
2.  Выберите тип проекта в раскрывающемся списке **версия целевого объекта миграции** , для которого необходимо просмотреть или изменить параметры, а затем щелкните вкладку **Общие** .  
  
3.  На левой панели щелкните **Преобразование**.  
  
4.  В области справа проверьте и при необходимости измените параметры. Дополнительные сведения об этих параметрах см. в разделе [Project settings &#40;Conversion&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
5.  Повторите шаги 1-3 для миграции, синхронизации, загрузки системных объектов, графического пользовательского интерфейса и сопоставления типов.  
  
    -   Сведения о параметрах миграции см. в разделе [Project settings &#40;migration&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md).  
  
    -   Сведения о параметрах системных объектов см. в разделе [Параметры проекта&#40;загрузке системных объектов&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md).  
  
    -   Сведения о параметрах синхронизации с см [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . в разделе [Project Settings&#40;Synchronization&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
    -   Сведения о параметрах графического пользовательского интерфейса см. в разделе [Project settings &#40;GUI&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md).  
  
    -   Сведения о параметрах сопоставления типов данных см. в разделе [Project settings &#40;Type mapping&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Чтобы перенести данные из баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо сначала создать проект.  
  
**Создание проекта**  
  
1.  В меню **Файл** выберите пункт **Создать проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В поле **Расположение** введите или выберите папку для проекта, а затем нажмите кнопку **ОК**.  
  
4.  В раскрывающемся списке **Миграция** выберите версию целевого объекта, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используемую для миграции. Доступны следующие варианты.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   БД SQL Azure  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Помимо определения параметров проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [Установка параметров проекта &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой базами данных можно определить сопоставления на уровне проекта, базы данных или объекта. Дополнительные сведения см. в разделе [Сопоставление типов данных Oracle и SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
При сохранении проекта SSMA сохраняет параметры проекта и при необходимости метаданные базы данных в файле проекта.  
  
**Сохранение проекта**  
  
-   В меню **файл** выберите команду **сохранить проект**.  
  
    Если схемы в проекте были изменены или не были преобразованы, SSMA предложит загрузить и сохранить метаданные. Загрузка и сохранение метаданных позволит работать в автономном режиме. Она также позволяет отправить полный файл проекта другим пользователям, например техническому персоналу службы технической поддержки. Если будет предложено сохранить метаданные, выполните следующие действия.  
  
    1.  Для каждой схемы, отображающей состояние **метаданных**, установите флажок рядом с именем базы данных.  
  
        Сохранение метаданных может занять несколько минут. Если вы не хотите сохранять метаданные, не выбирайте никакие флажки.  
  
    2.  Нажмите кнопку **Сохранить** .  
  
        SSMA будет анализировать схемы Oracle и сохранять метаданные в файл проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта он отключается от Oracle и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузите объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для переноса данных необходимо повторно подключиться к Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Открытие проекта**  
  
1.  Используйте одну из следующих процедур.  
  
    -   В меню **файл** укажите **последние проекты**, а затем щелкните проект, который нужно открыть.  
  
    -   В меню **файл** выберите **Открыть проект**, найдите файл проекта. o2ssproj, выберите файл и нажмите кнопку **Открыть**.  
  
2.  Чтобы повторно подключиться к Oracle, в меню **файл** выберите команду **Повторное подключение к Oracle**.  
  
3.  Чтобы повторно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в меню **файл** выберите команду **повторное подключение к SQL Server**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом процесса миграции является [Подключение к Oracle Database (OracleToSQL)](https://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
## <a name="see-also"></a>См. также:  
[Перенос баз данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[Подключение к Oracle Database &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[Подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
