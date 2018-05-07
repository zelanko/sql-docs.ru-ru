---
title: Работа с проектами SSMA (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Customizing Project Settings
ms.assetid: ee5d94c0-c7a6-4779-bd32-729bdaf61e1b
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 854d604680082375bba1d7fe5cca77d264ea7c9d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-ssma-projects-oracletosql"></a>Работа с проектами SSMA (OracleToSQL)
Для переноса баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создании проекта SSMA. Проект является файл, содержащий следующие сведения:  
  
-   Метаданные о базах данных Oracle, необходимо выполнить перенос [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Метаданные о целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , получат перенесенные объекты и данные.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сведения о соединении.  
  
-   Параметры проекта.  
  
При открытии проекта, он отключается от Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Позволяет работать в автономном режиме. Сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Просмотреть параметры проекта по умолчанию  
SSMA содержит несколько параметров, преобразования и загрузки объектов базы данных, перенос данных и синхронизации SSMA с Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Параметры по умолчанию подходят для многих пользователей. Тем не менее перед созданием нового проекта SSMA рекомендуется проверить параметры. Если вы хотите, можно изменить параметры по умолчанию, которые будут использоваться для новых проектов.  
  
**Чтобы просмотреть параметры проекта по умолчанию**  
  
1.  На **средства** меню, нажмите кнопку **параметры проекта по умолчанию**.  
  
2.  Выберите тип проекта в **миграции целевой версии** раскрывающийся список для просмотра или изменения требуются параметры, а затем нажмите кнопку **Общие** вкладки.  
  
3.  В левой области щелкните **преобразование**.  
  
4.  В правой области просмотрите и при необходимости измените параметры. Дополнительные сведения об этих параметрах см. в разделе [параметры проекта &#40;преобразования&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
5.  Повторите шаги 1 – 3 для миграции, синхронизации, загрузке системных объектов, графического пользовательского интерфейса и сопоставление типов страниц.  
  
    -   Сведения о миграции параметров см. в разделе [параметры проекта &#40;миграции&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md).  
  
    -   Сведения о настройках системы объекта см. в разделе [параметры проекта&#40;загрузке системных объектов&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md).  
  
    -   Дополнительные сведения о параметрах для синхронизации [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [параметры проекта&#40;синхронизации&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
    -   Сведения о параметрах графического пользовательского интерфейса см. в разделе [параметры проекта &#40;графического интерфейса пользователя&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md).  
  
    -   Сведения о параметрах сопоставление типов данных см. в разделе [параметры проекта &#40;сопоставление типов&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Для переноса данных из баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], необходимо сначала создать проект.  
  
**Создание проекта**  
  
1.  На **файл** меню, нажмите кнопку **новый проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В **расположение** введите или выберите папку для проекта и нажмите кнопку **ОК**.  
  
4.  В **миграции для** раскрывающийся список, выберите версию целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] используется для миграции. Доступны следующие варианты:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   База данных Azure SQL  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Кроме определения параметры проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [задание параметров проекта &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой баз данных, можно определить сопоставления на уровне объектов, базы данных или проекта. Дополнительные сведения см. в разделе [сопоставление Oracle и типы данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
При сохранении проекта SSMA сохраняет параметры проекта и при необходимости метаданных базы данных, в файл проекта.  
  
**Сохранение проекта**  
  
-   На **файл** меню, нажмите кнопку **сохранить проект**.  
  
    Если схем в проекте, были изменены или не был преобразован, SSMA предложит для загрузки и сохранения метаданных. Загрузка и сохранение метаданных позволит вам работать автономно. Он также позволяет отправить файл проекта для других пользователей, таких как сотрудники службы технической поддержки. Если будет предложено сохранить метаданные, выполните следующие действия.  
  
    1.  Для каждой схемы, показывающий состояние **отсутствует метаданных**, установите флажок рядом с именем базы данных.  
  
        Сохранение метаданных может занять несколько минут. Если вы не хотите сохранить метаданные, не устанавливайте флажки.  
  
    2.  Нажмите кнопку **Сохранить** кнопки.  
  
        SSMA проанализирует схемы Oracle и сохранять эти метаданные в файле проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта, он отключен от Oracle и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Для переноса данных, должны повторно подключиться к базе данных Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Чтобы открыть проект**  
  
1.  Используйте один из следующих процедур:  
  
    -   На **файл** последовательно выберите пункты **последние проекты**и выберите проект, который требуется открыть.  
  
    -   На **файл** последовательно выберите пункты **Открытие проекта**, найдите файл проекта .o2ssproj, выберите файл и нажмите кнопку **откройте**.  
  
2.  Для повторного подключения к базе данных Oracle, на **файл** меню, нажмите кнопку **повторное соединение с базой данных Oracle**.  
  
3.  Для повторного подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]на **файл** меню, нажмите кнопку **повторно подключиться к SQL Server**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции должно [подключение к базе данных Oracle (OracleToSQL)](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
## <a name="see-also"></a>См. также  
[Миграция Oracle баз данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[Подключение к базе данных Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[Подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
