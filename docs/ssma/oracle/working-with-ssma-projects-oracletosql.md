---
title: Работа с проектами SSMA (OracleToSQL) | Документация Майкрософт
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
manager: v-thobro
ms.openlocfilehash: 3ec3a2f9bcdf43657649263d77eff3b31c9a57a3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662724"
---
# <a name="working-with-ssma-projects-oracletosql"></a>Работа с проектами SSMA (OracleToSQL)
Для переноса баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], создании проекта SSMA. Проект — это файл, который содержит следующие сведения:  
  
-   Метаданные о базах данных Oracle, необходимо выполнить перенос [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Метаданные о целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , получат перенесенные объекты и данные.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения о соединении.  
  
-   Параметры проекта.  
  
При открытии проекта он отключен от Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это позволит вам работать в автономном режиме. Сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Просмотрев параметры проекта по умолчанию  
SSMA содержит несколько параметров для преобразования и загрузки объектов базы данных, перенос данных и синхронизации SSMA с Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметры по умолчанию подходят для многих пользователей. Тем не менее перед созданием нового проекта SSMA, рекомендуется проверить параметры. Если вы хотите, можно изменить параметры по умолчанию, которые будут использоваться для всех новых проектов.  
  
**Чтобы просмотреть параметры проекта по умолчанию**  
  
1.  На **средства** меню, щелкните **параметры проекта по умолчанию**.  
  
2.  Выберите тип проекта в **целевой версии миграции** раскрывающийся список, какие параметры необходимы для просмотра и изменения, а затем нажмите кнопку **Общие** вкладки.  
  
3.  В левой области щелкните **преобразования**.  
  
4.  В правой области просмотрите и при необходимости измените параметры. Дополнительные сведения об этих параметрах см. в разделе [параметры проекта &#40;преобразования&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
5.  Повторите шаги 1 – 3 для миграции, синхронизации, загрузка системных объектов, графического пользовательского интерфейса и сопоставления типов страниц.  
  
    -   Сведения о параметрах миграции см. в разделе [параметры проекта &#40;миграции&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md).  
  
    -   Сведения о параметрах системы объекта см. в разделе [параметры проекта&#40;Загрузка системных объектов&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md).  
  
    -   Сведения о параметрах для синхронизации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [параметры проекта&#40;синхронизации&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
    -   Сведения о параметрах графического пользовательского интерфейса см. в разделе [параметры проекта &#40;графического пользовательского интерфейса&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md).  
  
    -   Сведения о параметрах сопоставление типов данных см. в разделе [параметры проекта &#40;сопоставление типов&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Для переноса данных из баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо сначала создать проект.  
  
**Создание проекта**  
  
1.  На **файл** меню, щелкните **новый проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В **расположение** введите или выберите папку для проекта и нажмите кнопку **ОК**.  
  
4.  В **миграции для** раскрывающийся список, выберите версию целевого сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для миграции. Доступны следующие варианты:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   База данных Azure SQL  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Кроме определения параметров проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [Настройка параметров проекта &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой баз данных, можно определить сопоставлений на уровне объекта, базы данных или проекта. Дополнительные сведения см. в разделе [сопоставление Oracle и типы данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
При сохранении проекта SSMA сохраняет параметры проекта и при необходимости метаданных базы данных, в файл проекта.  
  
**Сохранение проекта**  
  
-   На **файл** меню, щелкните **сохранить проект**.  
  
    Если схемы в проекте, были изменены или не были преобразованы, SSMA предложит для загрузки и сохранения метаданных. Загрузки и сохранения метаданных можно работать в автономном режиме. Это также позволяет отправить файл проекта для других пользователей, например отдела технической поддержки. Если вам будет предложено сохранить метаданные, сделайте следующее:  
  
    1.  Для каждой схемы, отобразится состояние **отсутствующими метаданными**, установите флажок рядом с именем базы данных.  
  
        Сохранение метаданных может занять несколько минут. Если вы не хотите сохранить метаданные, не устанавливайте флажки.  
  
    2.  Нажмите кнопку **Сохранить** кнопки.  
  
        SSMA проанализирует схем Oracle и сохраните файл метаданных в файл проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта, он отключен от Oracle и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это позволит вам работать в автономном режиме. Чтобы обновить метаданные, загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы перенести данные, необходимо повторно подключиться к базе данных Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Открытие проекта**  
  
1.  Используйте один из следующих процедур.  
  
    -   На **файл** последовательно выберите пункты **последние проекты**и выберите проект, который требуется открыть.  
  
    -   На **файл** меню, выберите **Открытие проекта**, найдите файл проекта .o2ssproj, выберите файл и нажмите кнопку **откройте**.  
  
2.  Для повторного подключения к базе данных Oracle, на **файл** меню, щелкните **повторное соединение с базой данных Oracle**.  
  
3.  Чтобы повторно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]на **файл** меню, щелкните **повторно подключиться к SQL Server**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе миграции является [подключение к базе данных Oracle (OracleToSQL)](https://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
## <a name="see-also"></a>См. также  
[Переход с Oracle баз данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[Подключение к базе данных Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[Подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
