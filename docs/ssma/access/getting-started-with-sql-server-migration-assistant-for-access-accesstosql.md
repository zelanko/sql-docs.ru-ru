---
title: Начало работы с Помощник по миграции SQL Server для доступа | Документация Майкрософт
description: Приступая к работе с SSMA для преобразования объектов базы данных Access в SQL Server или объекты базы данных SQL Azure, передачи результирующих объектов и переноса данных.
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- error list pane
- getting started
- menus
- metadata explorers
- output pane
- toolbars
- user interface
- user interface overview
ms.assetid: 462a731f-08f1-44e1-9eeb-4deac6d2f6c5
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: d622396e9e650aa3e9fc1b3855e1dfc1634bc34e
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938843"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Начало работы с Помощник по миграции SQL Server для доступа (Акцесстоскл)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) для Access позволяет быстро преобразовывать объекты базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure, передавать полученные объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure и выполнять перенос данных из Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или из нее. При необходимости можно также связать таблицы доступа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или таблицы базы данных SQL Azure, чтобы вы могли продолжать использовать существующие клиентские приложения Access с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базой данных SQL Azure.  
  
В этом разделе описывается процесс установки и помогает ознакомиться с пользовательским интерфейсом SSMA.  
  
## <a name="installing-ssma"></a>Установка SSMA  
Чтобы использовать SSMA, необходимо сначала установить клиентскую программу SSMA на компьютере, который может получить доступ как к базам данных, которые необходимо перенести, так и к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Инструкции по установке см. в разделе [установка помощник по миграции SQL Server для Access &#40;акцесстоскл&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Чтобы запустить SSMA, нажмите кнопку **Пуск**, укажите пункт **все программы**, выберите **Помощник по миграции SQL Server для доступа**, а затем выберите **Помощник по миграции SQL Server для доступа**.  
  
## <a name="using-ssma"></a>Использование SSMA  
После установки SSMA помогает ознакомиться с пользовательским интерфейсом SSMA, прежде чем использовать средство для переноса баз данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. Пользовательский интерфейс SSMA, включая обозреватели метаданных, метаданные, панели инструментов, панель вывода и список ошибок, показан на следующей схеме:  
  
![SSMA для графического интерфейса пользователя Access](../../ssma/access/media/ssmaforaccessgui.gif "SSMA для графического интерфейса пользователя Access")  
  
Чтобы начать миграцию, создайте новый проект, а затем добавьте базы данных Access для доступа к обозревателю метаданных. Затем можно щелкнуть правой кнопкой мыши объекты в обозревателе метаданных Access, чтобы выполнить следующие задачи:
- Экспорт перечня объектов базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или.
- Создание отчетов, оценивающих преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или.
- Преобразование схем доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы базы данных SQL Azure или.

Эти задачи также можно выполнить с помощью панелей инструментов и меню.  
  
Необходимо также подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После успешного подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в обозревателе метаданных отобразится иерархия баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После преобразования схем доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы можно выбрать эти преобразованные схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателе метаданных, а затем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Если вы выбрали базу данных SQL Azure в диалоговом окне Миграция в раскрывающийся список в новом проекте, необходимо подключиться к базе данных SQL Azure. После успешного подключения в обозревателе метаданных базы данных SQL Azure отобразится иерархия баз данных SQL Azure. После преобразования схем доступа в схемы базы данных SQL Azure можно выбрать эти преобразованные схемы в обозревателе метаданных базы данных SQL Azure, а затем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
После загрузки преобразованных схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или из нее можно вернуться к обозревателю метаданных и перенести данные из баз данных Access в базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure или из них. При необходимости можно также связать таблицы доступа с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицами базы данных SQL Azure или.  
  
Дополнительные сведения об этих задачах и способах их выполнения см. в следующих разделах:  
  
-   [Подготовка баз данных Access к миграции](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Связывание приложений Access с SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
В следующих разделах описываются функции пользовательского интерфейса SSMA.  
  
### <a name="metadata-explorers"></a>Обозреватель метаданных  
SSMA содержит два обозревателя метаданных, которые можно использовать для просмотра и выполнения действий в базах данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных SQL Azure.  
  
#### <a name="access-metadata-explorer"></a>Доступ к обозревателю метаданных  
В обозревателе метаданных Access отображаются сведения о базах данных Access, которые были добавлены в проект. При добавлении базы данных Access SSMA извлекает метаданные об этой базе данных, которая является метаданными, доступными в обозревателе метаданных Access.  
  
С помощью обозревателя метаданных Access можно выполнять следующие задачи.  
  
-   Просмотрите таблицы в каждой базе данных Access.  
  
-   Выберите объекты для преобразования и преобразуйте объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис. Дополнительные сведения см. в разделе [Преобразование объектов базы данных Access](converting-access-database-objects-accesstosql.md).  
  
-   Выберите объекты для переноса данных и перенесите данные из этих объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. [в разделе Перенос данных Access в SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Связывание и отмена связи доступа и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблиц.  
  
#### <a name="sql-server-or-azure-sql-database-metadata-explorer"></a>SQL Server или обозреватель метаданных базы данных SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или обозреватель метаданных базы данных SQL Azure отображает сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
Вы можете использовать SQL Server или обозреватель метаданных базы данных SQL Azure, чтобы выбрать преобразованные объекты базы данных Access и загрузить (синхронизировать) эти объекты в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure.  
  
Дополнительные сведения см. [в разделе Загрузка преобразованных объектов базы данных в SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозревателя метаданных находятся вкладки, описывающие выбранный объект. Например, если выбрать таблицу в обозревателе метаданных Access, отобразятся четыре вкладки: **Таблица**, **Сопоставление типов**, **Свойства**и **данные**. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателе метаданных, отобразятся три вкладки: **Таблица**, **SQL**и **данные**.  
  
Большинство параметров метаданных доступны только для чтения. Однако можно изменить следующие метаданные:  
  
-   В обозревателе метаданных Access можно изменять сопоставления типов. Не забудьте внести эти изменения перед созданием отчетов или преобразованием схем.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателе метаданных можно изменить свойства таблицы и индекса на вкладке **Таблица** . Внесите эти изменения перед загрузкой схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Преобразование объектов базы данных Access](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA содержит две панели инструментов: панель инструментов проекта и панель инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панель инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, добавления файлов базы данных Access и подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных SQL Azure. Эти кнопки похожи на команды в меню **файл** .  
  
#### <a name="the-migration-toolbar"></a>Панель инструментов миграции  
Панель инструментов миграции содержит следующие команды:  
  
|Кнопка|Функция|  
|----------|------------|  
|**Преобразование, загрузка и миграция**|Преобразует базы данных Access, загружает преобразованные объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure и переносит их в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure и все за один шаг.|  
|**Создавать отчет**|Преобразует выбранную схему доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure, а затем создает отчет, показывающий, как было выполнено преобразование.<br /><br />Эта команда доступна, только если объекты выбраны в обозревателе метаданных Access.|  
|**Преобразовать схему**|Преобразует выбранную схему доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы базы данных SQL Azure или.<br /><br />Эта команда доступна, только если объекты выбраны в обозревателе метаданных Access.|  
|**Перенос данных**|Переносит данные из базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. Перед выполнением этой команды необходимо преобразовать схемы доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы базы данных SQL Azure или в нее, а затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure.<br /><br />Эта команда доступна, только если объекты выбраны в обозревателе метаданных Access.|  
|**Остановить**|Останавливает текущий процесс, например преобразование объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure.|  
  
### <a name="menus"></a>Меню  
SSMA содержит следующие меню:  
  
|Меню|Описание|  
|--------|---------------|  
|**Файл**|Содержит команды для мастера миграции, работы с проектами, добавления и удаления файлов базы данных Access, а также подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных SQL Azure.|  
|**Edit** (Изменение)|Содержит команды для поиска и работы с текстом на страницах со сведениями, например для копирования [!INCLUDE[tsql](../../includes/tsql-md.md)] из области сведений о SQL. Чтобы открыть диалоговое окно **Управление закладками** , в меню Правка выберите пункт Управление закладками. В диалоговом окне вы увидите список существующих закладок. Для управления закладками можно использовать кнопки в правой части диалогового окна.|  
|**Просмотр**|Содержит команду **Синхронизация обозревателей метаданных** . Это синхронизирует объекты между обозревателем метаданных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателем метаданных базы данных SQL Azure. Также содержит команды для отображения и скрытия **выходных** и **Список ошибок** панелей и **макетов** параметров для управления с помощью макетов.|  
|**Инструменты**|Содержит команды для создания отчетов, экспорта данных, переноса объектов и данных, связывания таблиц и доступа к диалоговым окнам глобальные и параметры проекта.|  
|**Справка**|Предоставляет доступ к справке SSMA и диалоговому окну " **о программе** ".|  
  
### <a name="output-pane-and-error-list-pane"></a>Область вывода и область Список ошибок  
Меню **вид** содержит команды для переключения видимости области вывода и список ошибок панели.  
  
-   В области вывода отображаются сообщения о состоянии от SSMA во время преобразования объектов, синхронизации объектов и переноса данных.  
  
-   В области Список ошибок отображаются сообщения об ошибках, предупреждениях и информационном списке, которые можно сортировать.  
  
## <a name="see-also"></a>См. также статью  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
