---
title: Работа с проектами SSMA (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: eb6f035b4d597e2b648134c195b698554dc78e12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072469"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Работа с проектами SSMA (SybaseToSQL)
Для переноса баз данных Sybase Adaptive Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, вы сначала Создание проекта SSMA. Проект — это файл, который содержит метаданные о базах данных ASE, которые вы хотите перейти на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, метаданные о целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, который будет получать перенесенные объекты и данные, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure сведения о подключении и параметры проекта.  
  
При открытии проекта он отключен от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Это позволяет работать в автономном режиме. Вы можете заново подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Дополнительные сведения см. в разделе [подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Просмотрев параметры проекта по умолчанию  
SSMA содержит несколько вариантов преобразование и загрузка объектов базы данных, перенос данных и синхронизацией SSMA с ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Параметры по умолчанию для этих параметров подходят для многих пользователей. Тем не менее перед созданием нового проекта SSMA, следует ознакомиться с вариантами и, если вы хотите, изменить значения по умолчанию, которые будут использоваться для всех новых проектов.  
  
**Чтобы просмотреть параметры проекта по умолчанию**  
  
1.  На **средства** меню, выберите **параметры проекта по умолчанию**.  
  
2.  Выберите тип проекта в **целевой версии миграции** раскрывающийся список, какие параметры необходимы для просмотра и изменения, а затем нажмите кнопку **Общие** вкладки.  
  
3.  В левой области щелкните **преобразования**.  
  
4.  В правой области просмотрите параметры, изменив параметры по необходимости. Дополнительные сведения об этих параметрах см. в разделе [параметры проекта &#40;преобразования&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Повторите шаги 1 – 3 для миграции SQL Azure, загрузка объектов, графического пользовательского интерфейса и сопоставления типов страниц.  
  
    -   Сведения о параметрах миграции см. в разделе [параметры проекта &#40;миграции&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах для загрузки объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [параметры проекта &#40;синхронизации&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах графического пользовательского интерфейса, см. в разделе [параметры проекта &#40;графического пользовательского интерфейса&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах сопоставление типов данных [параметры проекта &#40;сопоставление типов&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах SQL Azure, см. в разделе [параметры проекта &#40;базы данных SQL Azure &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Параметры SQL Azure будет отображаться только в том случае, когда вы выбираете **миграции в SQL Azure** при создании проекта.  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Для переноса данных из баз данных ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, необходимо сначала создать проект.  
  
**Создание проекта**  
  
1.  В меню **Файл** выберите пункт **Создать проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В **расположение** введите или выберите папку для проекта.  
  
4.  В **миграции для** раскрывающийся список, выберите версию целевого сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для миграции. Доступны следующие варианты:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   БД SQL Azure  
  
А затем нажмите кнопку **ОК**.  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Кроме определения параметров проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [Настройка параметров проекта &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой баз данных, можно определить сопоставлений на уровне объекта, базы данных или проекта. Дополнительные сведения о сопоставлении типов см. в разделе [сопоставление Sybase ASE и типы данных SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
При сохранении проекта SSMA сохраняет параметры проекта и при необходимости метаданных базы данных, в файл проекта.  
  
**Сохранение проекта**  
  
-   На **файл** меню, выберите **сохранить проект**.  
  
    Если базы данных в рамках проекта были изменены или не были преобразованы, SSMA предложит сохранить метаданные в проект. Сохранение метаданных можно работать в автономном режиме и для отправки файла проекта для других пользователей, включая отдела технической поддержки. Если вам будет предложено сохранить метаданные, сделайте следующее:  
  
    1.  Для каждой базы данных, который отображается состояние **отсутствующими метаданными**, установите флажок рядом с именем базы данных.  
  
        Сохранение метаданных может занять несколько минут. Если вы не хотите сохранить метаданные на этом этапе, не устанавливайте флажки.  
  
    2.  Нажмите кнопку **Сохранить**.  
  
        SSMA проанализирует схем Sybase ASE и сохраните файл метаданных в файл проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта он отключен из ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Это позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Чтобы перенести данные, должны повторно подключиться к среде ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
**Открытие проекта**  
  
1.  Используйте один из следующих процедур.  
  
    -   На **файл** последовательно выберите пункты **последние проекты**, а затем выберите проект, который требуется открыть.  
  
    -   На **файл** меню, выберите **Открытие проекта**, найдите файл проекта .s2ssproj, выберите файл и нажмите кнопку **откройте**.  
  
2.  Чтобы повторно подключиться к среде службы Приложений, на **файл** меню, выберите **повторное подключение к Sybase**.  
  
3.  Чтобы повторно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, на **файл** меню, выберите **повторно подключиться к SQL Server** / **повторно подключиться к SQL Azure**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе миграции является [подключение к Sybase ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Подключение к Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Подключение к базе данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
