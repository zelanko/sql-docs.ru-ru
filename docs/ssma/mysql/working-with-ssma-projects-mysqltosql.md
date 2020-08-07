---
title: Работа с проектами SSMA (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Working with SSMA projects, create new project
- Working with SSMA projects, customize settings
- Working with SSMA projects, Open project
- Working with SSMA projects, Save project
ms.assetid: 9e4394e9-f177-41d9-839e-5d53a9c9b840
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2d9bec916103214169f549a0b555a46fd0d65fdb
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862495"
---
# <a name="working-with-ssma-projects-mysqltosql"></a>Работа с проектами SSMA (MySQLToSQL)
Чтобы перенести базы данных MySQL в SQL Server или SQL Azure, необходимо сначала создать проект SSMA. Проект представляет собой файл, содержащий следующие сведения:  
  
-   Метаданные о базах данных MySQL, которые необходимо перенести в SQL Server или SQL Azure.  
  
-   Метаданные о целевом экземпляре SQL Server или SQL Azure, который будет принимать перенесенные объекты и данные.  
  
-   SQL Server или SQL Azure сведения о соединении.  
  
-   Параметры проекта.  
  
При открытии проекта он отключается от MySQL, SQL Server или SQL Azure. Это позволяет работать в автономном режиме. Дополнительные сведения о повторном подключении к SQL Server см. [в разделе Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="reviewing-default-project-settings"></a>Просмотр параметров проекта по умолчанию  
SSMA содержит несколько параметров для преобразования и загрузки базы данных, переноса данных и синхронизации SSMA с MySQL, SQL Server или SQL Azure. Параметры по умолчанию подходят для многих пользователей. Однако перед созданием нового проекта SSMA необходимо проверить параметры. При необходимости можно изменить параметры по умолчанию, которые будут использоваться для всех новых проектов.  
  
##### <a name="to-review-default-project-settings"></a>Проверка параметров проекта по умолчанию  
  
1.  Выберите **Параметры проекта по умолчанию** в меню **Сервис** .  
  
2.  Выберите тип проекта в раскрывающемся списке **версия целевого объекта миграции** , для которого необходимо просмотреть или изменить параметры, а затем щелкните вкладку **Общие** .  
  
3.  На левой панели щелкните **Преобразование**.  
  
4.  В области справа проверьте и при необходимости измените параметры. Дополнительные сведения об этих параметрах см. в разделе [Project settings &#40;Conversion&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md) .  
  
5.  Повторите шаги 1-3 для страниц "миграция", "Синхронизация", "SQL Azure, графический интерфейс пользователя" и "сопоставление типов".  
  
-   Сведения о параметрах миграции см. в разделе [Project settings &#40;migration&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md).  
  
-   Сведения о параметрах синхронизации с SQL Server см. в разделе [Project settings &#40;Synchronization&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md).  
  
-   Сведения о параметрах графического пользовательского интерфейса см. в разделе [Параметры проекта (графический интерфейс пользователя) (SSMA Common)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
-   Сведения о параметрах сопоставления типов данных см. в разделе [Project settings &#40;Type mapping&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
-   Сведения о параметрах SQL Azure см. в разделе [Параметры проекта &#40;база данных SQL Azure&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md).  
  
> [!NOTE]  
> Параметры SQL Azure будут отображаться только при выборе параметра **миграция для SQL Azure** при создании проекта.  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Чтобы перенести данные из баз данных MySQL в SQL Server или SQL Azure, необходимо создать проект.  
  
##### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  В меню **файл** выберите пункт **создать проект** . Откроется диалоговое окно **Новый проект** . В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Новый проект** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В поле **Расположение** введите или выберите папку для проекта.  
  
4.  В раскрывающемся списке **Миграция** выберите версию целевого объекта, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используемую для миграции. Доступны следующие варианты.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014  
  
    -   База данных SQL Azure  
  
И нажмите кнопку **ОК** .  
  
SSMA создает файл проекта.  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Помимо определения параметров проекта по умолчанию, которые применяются ко всем новым проектам SSMA, можно также настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [Установка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).  
  
При настройке сопоставлений типов данных между исходной и целевой базами данных можно определить сопоставления на уровне проекта, базы данных или объекта. Дополнительные сведения см. в разделе [Сопоставление типов данных MySQL и SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
Функция сохранения проектов позволяет пользователю сохранять параметры проекта и, при необходимости, метаданные базы данных в файле проекта SSMA.  
  
##### <a name="to-save-a-project"></a>Сохранение проекта  
  
-   В меню **файл** выберите команду **сохранить** проект.  
  
Если базы данных в проекте были изменены или не были преобразованы, SSMA предложит загрузить и сохранить метаданные. Загрузка и сохранение метаданных позволяет работать в автономном режиме. Она также позволяет отправить полный файл проекта другим пользователям, например техническому персоналу службы технической поддержки. Если будет предложено сохранить метаданные, выполните следующие действия.  
  
1.  Для каждой базы данных, в которой не **указано состояние метаданных**, установите флажок рядом с именем базы данных. Сохранение метаданных может занять несколько минут. Если вы не хотите сохранять метаданные на этом этапе, не выбирайте никакие флажки.  
  
2.  Щелкните **Сохранить**.  
  
SSMA будет анализировать схемы MySQL и сохранять метаданные в файл проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта он отключается от MySQL, а также из SQL Server или SQL Azure. Это позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузите объекты базы данных в SQL Server или SQL Azure. Чтобы перенести данные, необходимо повторно подключиться к SQL Server или SQL Azure.  
  
##### <a name="to-open-a-project"></a>Открытие проекта  
  
1.  Используйте одну из следующих процедур.  
  
    1.  В меню **файл** укажите пункт **Недавние проекты**.  
  
    2.  Выберите проект, который необходимо открыть.  
  
    3.  В меню **файл** выберите **Открыть проект**, найдите файл проекта. m2ssproj, выберите файл и нажмите кнопку **Открыть**.  
  
2.  Чтобы повторно подключиться к MySQL, в меню **файл** выберите команду **Повторное подключение к MySQL**.  
  
3.  Чтобы повторно подключиться к SQL Server, в меню **файл** выберите команду **Повторное подключение к SQL Server**.  
  
4.  Чтобы повторно подключиться к SQL Azure, в меню **файл** выберите команду **Повторное подключение к SQL Azure.**  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом процесса миграции является [Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
## <a name="see-also"></a>См. также:  
[Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
[Перенос баз данных MySQL в SQL Server базы данных SQL Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
[Подключение к базе данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
