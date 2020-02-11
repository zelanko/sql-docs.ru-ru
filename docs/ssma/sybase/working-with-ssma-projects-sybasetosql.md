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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68072469"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Работа с проектами SSMA (SybaseToSQL)
Чтобы выполнить миграцию баз данных адаптивного сервера предприятия ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ASE) в или SQL Azure, сначала необходимо создать проект SSMA. Проект — это файл, содержащий метаданные о базах данных ASE, которые необходимо перенести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, метаданные о целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, которые будут принимать перенесенные объекты и данные, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] а также SQL Azure сведения о соединении и параметры проекта.  
  
При открытии проекта он отключается от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Это позволяет работать в автономном режиме. Вы можете повторно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Дополнительные сведения см. в статьях [Подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  /  [Подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Просмотр параметров проекта по умолчанию  
SSMA содержит несколько параметров для преобразования и загрузки объектов базы данных, переноса данных и синхронизации SSMA с ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Параметры по умолчанию для этих параметров подходят для многих пользователей. Однако перед созданием нового проекта SSMA следует ознакомиться с параметрами и, при необходимости, изменить значения по умолчанию, которые будут использоваться для всех новых проектов.  
  
**Проверка параметров проекта по умолчанию**  
  
1.  В меню **Сервис** выберите пункт **Параметры проекта по умолчанию**.  
  
2.  Выберите тип проекта в раскрывающемся списке **версия целевого объекта миграции** , для которого необходимо просмотреть или изменить параметры, а затем щелкните вкладку **Общие** .  
  
3.  На левой панели щелкните **Преобразование**.  
  
4.  На правой панели проверьте параметры, изменяя параметры по мере необходимости. Дополнительные сведения об этих параметрах см. в разделе [Project Settings &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Повторите шаги 1-3 для миграции, SQL Azure, загрузки объектов, графического пользовательского интерфейса и сопоставления типов.  
  
    -   Сведения о параметрах миграции см. в разделе [Project Settings &#40;migration&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Сведения о параметрах загрузки объектов в см [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. в разделе [Project Settings &#40;Synchronization&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах графического пользовательского интерфейса см. в разделе [Project Settings &#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Чтобы получить дополнительные сведения о параметрах сопоставления типов данных, щелкните [Параметры проекта &#40;сопоставление типов&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Дополнительные сведения о параметрах SQL Azure см. в разделе [Параметры проекта &#40;база данных SQL Azure &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Параметры SQL Azure будут отображаться только при выборе параметра **миграция для SQL Azure** при создании проекта.  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Чтобы перенести данные из баз данных ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в или SQL Azure, необходимо сначала создать проект.  
  
**Создание проекта**  
  
1.  В меню **Файл** выберите пункт **Создать проект**.  
  
    Раскроется диалоговое окно **Новый проект**.  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В поле **Расположение** введите или выберите папку для проекта.  
  
4.  В раскрывающемся списке **Миграция** выберите версию целевого объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемую для миграции. Доступны следующие варианты.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016  
  
    -   БД SQL Azure  
  
И нажмите кнопку **ОК**.  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Помимо определения параметров проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [Установка параметров проекта &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой базами данных можно определить сопоставления на уровне проекта, базы данных или объекта. Дополнительные сведения о сопоставлении типов см. в разделе [Mapping SYBASE ASE and SQL Server Data types &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
При сохранении проекта SSMA сохраняет параметры проекта и при необходимости метаданные базы данных в файле проекта.  
  
**Сохранение проекта**  
  
-   В меню **файл** выберите команду **сохранить проект**.  
  
    Если базы данных в проекте были изменены или не были преобразованы, SSMA предложит сохранить метаданные в проекте. Сохранение метаданных позволит работать в автономном режиме и отправить полный файл проекта другим пользователям, включая службу технической поддержки. Если будет предложено сохранить метаданные, выполните следующие действия.  
  
    1.  Для каждой базы данных, в которой не **указано состояние метаданных**, установите флажок рядом с именем базы данных.  
  
        Сохранение метаданных может занять несколько минут. Если вы не хотите сохранять метаданные на этом этапе, не выбирайте никакие флажки.  
  
    2.  Нажмите кнопку **Сохранить**.  
  
        SSMA выполнит синтаксический анализ схем Sybase ASE и сохранит метаданные в файле проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта он отключается от ASE, а также из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Это позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузите объекты базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в или SQL Azure. Чтобы перенести данные, необходимо повторно подключиться к ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
**Открытие проекта**  
  
1.  Используйте одну из следующих процедур.  
  
    -   В меню **файл** укажите **последние проекты**, а затем выберите проект, который нужно открыть.  
  
    -   В меню **файл** выберите **Открыть проект**, найдите файл проекта. s2ssproj, выберите файл и нажмите кнопку **Открыть**.  
  
2.  Чтобы повторно подключиться к ASE, в меню **файл** выберите команду **Повторное подключение к Sybase**.  
  
3.  Чтобы повторно подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, в меню **файл** выберите команду **Повторное подключение, чтобы SQL Server** / **повторно подключиться к SQL Azure**.  
  
## <a name="next-step"></a>Дальнейшее действие  
Следующим шагом процесса миграции является [Подключение к SYBASE ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Sybase ASE в SQL Server Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Подключение к Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
