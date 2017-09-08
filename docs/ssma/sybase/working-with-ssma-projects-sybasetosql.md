---
title: "Работа с проектами SSMA (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 957f4148fc200fee98b29fed1f28a17bc8661d07
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="working-with-ssma-projects-sybasetosql"></a>Работа с проектами SSMA (SybaseToSQL)
Для переноса баз данных Sybase адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, сначала создайте SSMA проект. Проект является файл, содержащий метаданные о ASE баз данных, которые необходимо выполнить перенос [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, метаданные о целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, который получит перенесенные объекты и данные, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или сведения о соединении SQL Azure и параметры проекта.  
  
При открытии проекта, он отключается от [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Это позволяет работать в автономном режиме. Вы можете заново подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Дополнительные сведения см. в разделе [подключение к SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  /  [Подключения к БД Azure SQL &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Просмотреть параметры проекта по умолчанию  
SSMA содержит несколько параметров, преобразования и загрузки объектов базы данных, перенос данных и синхронизации SSMA с ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Параметры по умолчанию для этих параметров подходят для многих пользователей. Тем не менее перед созданием нового проекта SSMA необходимо просмотреть параметры и, если требуется, изменить значения по умолчанию, которые будут использоваться для новых проектов.  
  
**Чтобы просмотреть параметры проекта по умолчанию**  
  
1.  На **средства** последовательно выберите пункты **параметры проекта по умолчанию**.  
  
2.  Выберите тип проекта в **миграции целевой версии** раскрывающийся список для просмотра или изменения требуются параметры, а затем нажмите кнопку **Общие** вкладки.  
  
3.  В левой области щелкните **преобразование**.  
  
4.  В правой области просмотрите параметры, изменив параметры по необходимости. Дополнительные сведения об этих параметрах см. в разделе [параметры проекта &#40; Преобразование &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Повторите шаги 1 – 3 для миграции, SQL Azure, загрузка объектов, графического пользовательского интерфейса и сопоставление типов страниц.  
  
    -   Сведения о параметрах миграции см. в разделе [параметры проекта &#40; Миграция &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах для загрузки объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [параметры проекта &#40; Синхронизация &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах графического пользовательского интерфейса см. в разделе [параметры проекта &#40; GUI &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах сопоставление типов данных [параметры проекта &#40; Сопоставление типов &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах SQL Azure см. в разделе [параметры проекта &#40; База данных Azure SQL &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Параметры SQL Azure будет отображаться только при выборе **миграцию в SQL Azure** при создании проекта.  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Для переноса данных из базы данных ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, необходимо сначала создать проект.  
  
**Создание проекта**  
  
1.  В меню **Файл** выберите пункт **Создать проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В **расположение** введите или выберите папку для проекта.  
  
4.  В **миграции для** раскрывающийся список, выберите версию целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] используется для миграции. Доступны следующие варианты:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   База данных Azure SQL  
  
Затем **ОК**.  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Кроме определения параметры проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [задание параметров проекта &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой баз данных, можно определить сопоставления на уровне объектов, базы данных или проекта. Дополнительные сведения о сопоставлении типов см. в разделе [сопоставления Sybase ASE и типов данных SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
При сохранении проекта SSMA сохраняет параметры проекта и при необходимости метаданных базы данных, в файл проекта.  
  
**Сохранение проекта**  
  
-   На **файл** последовательно выберите пункты **сохранить проект**.  
  
    Если базы данных в проекте, были изменены или не был преобразован, SSMA предложит сохранить метаданные в проект. Сохранение метаданных позволит вам работать автономно и отправка файла проекта для других пользователей, включая службу технической поддержки. Если будет предложено сохранить метаданные, выполните следующие действия.  
  
    1.  Для каждой базы данных, который показывает состояние **отсутствует метаданных**, установите флажок рядом с именем базы данных.  
  
        Сохранение метаданных может занять несколько минут. Если вы не хотите сохранить метаданные на этом этапе, не устанавливайте флажки.  
  
    2.  Нажмите кнопку **Сохранить** кнопки.  
  
        SSMA проанализирует Sybase ASE схем и сохранения этих метаданных в файле проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта, он отключен от ASE и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Это позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Для переноса данных, необходимо повторно подключится ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
**Чтобы открыть проект**  
  
1.  Используйте один из следующих процедур:  
  
    -   На **файл** последовательно выберите пункты **последние проекты**, а затем выберите проект, который требуется открыть.  
  
    -   На **файл** последовательно выберите пункты **Открытие проекта**, найдите файл проекта .s2ssproj, выберите файл и нажмите кнопку **откройте**.  
  
2.  Чтобы повторно подключиться к ASE, на **файл** последовательно выберите пункты **повторно подключиться к Sybase**.  
  
3.  Для повторного подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure на **файл** последовательно выберите пункты **повторно подключиться к SQL Server** / **повторно подключиться к SQL Azure**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции должно [соединиться Sybase ASE](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Подключение к Sybase ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Подключение к SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Подключение к Azure SQL DB &#40; SybaseToSQL &#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  

