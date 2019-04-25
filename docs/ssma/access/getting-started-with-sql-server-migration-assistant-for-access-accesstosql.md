---
title: Начало работы с SQL Server Migration Assistant для Access | Документация Майкрософт
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
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 1168609d35a266f2ac5fe6641aee7ca131bc9d89
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62759928"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Приступая к работе с SQL Server Migration Assistant для Access (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для доступа позволяет быстро преобразовать объектов базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure, отправьте полученные объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, и перенести данные с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. При необходимости можно также связать доступа к таблицам для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или таблицы базы данных SQL Azure, таким образом, можно продолжать использовать существующие приложения Access переднего плана с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure.  
  
В этом разделе представлен процесс установки и позволяет ознакомиться с пользовательским интерфейсом SSMA.  
  
## <a name="installing-ssma"></a>Установка SSMA  
Чтобы использовать SSMA, сначала необходимо установить SSMA клиентскую программу на компьютере с доступом к одновременно в базах данных, которые требуется перенести и на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Инструкции по установке см. в разделе [Установка SQL Server Migration Assistant для Access &#40;AccessToSQL&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Для запуска SSMA, нажмите кнопку **запустить**, пункты **все программы**, пункты **SQL Server Migration Assistant для Access**, а затем выберите **переход на SQL Server Помощник по службам для доступа к**.  
  
## <a name="using-ssma"></a>С помощью SSMA  
После установки SSMA, полезно ознакомиться с пользовательским интерфейсом SSMA перед использованием средства миграции баз данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Пользовательский интерфейс SSMA, включая обучающие ресурсы для метаданных, метаданные, панелей инструментов, область вывода и область списка ошибок, показаны на следующей схеме.  
  
![SSMA для графического интерфейса пользователя Access](../../ssma/access/media/ssmaforaccessgui.gif "SSMA для графического интерфейса пользователя Access")  
  
Чтобы начать миграцию, создайте новый проект и затем добавить доступ обозреватель метаданных базы данных Access. Затем щелкнуть правой кнопкой мыши объекты в обозревателе метаданных доступ для выполнения задач, таких как:
- Экспорт актуальный список объектов базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure.
- Создание отчетов, которые оценивают преобразования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure.
- Преобразование схем доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure.

Эти задачи также можно выполнить с помощью панели инструментов и меню.  
  
Также необходимо подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После успешного подключения иерархию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных отображается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. После преобразования схем доступа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы, можно выбрать преобразованный схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, а затем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
При выборе базы данных SQL Azure из миграции в раскрывающемся списке в диалоговом окне "новый проект", необходимо подключиться к базе данных SQL Azure. После успешного подключения баз данных Azure SQL DB. Иерархия выглядит в обозревателе метаданных базы данных SQL Azure. После преобразования схемы доступа к схемам базы данных SQL Azure, можно выбрать преобразованный схемы в обозревателе метаданных базы данных SQL Azure и затем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
После загрузки схем, преобразованное в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, можно вернуться в обозреватель метаданных доступа и переноса данных из базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базах данных SQL Azure. При необходимости можно также связать доступа к таблицам для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или таблиц базы данных SQL Azure.  
  
Дополнительные сведения об этих задачах и порядок их выполнения см. в разделах:  
  
-   [Подготовка к миграции базы данных Access](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Связь приложений Access SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
Ниже описаны возможности пользовательского интерфейса SSMA.  
  
### <a name="metadata-explorers"></a>Обучающие ресурсы для метаданных  
SSMA содержит два обозревателей метаданные, которые можно использовать для просмотра и выполнения действий на доступ и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базах данных SQL Azure.  
  
#### <a name="access-metadata-explorer"></a>Доступ к обозревателю метаданных  
Обозреватель метаданных доступа отображаются сведения о базы данных Access, которые были добавлены в проект. При добавлении базы данных Access, SSMA извлекает метаданные об этой базе данных метаданные, доступные в обозревателе метаданных доступа.  
  
Обозреватель метаданных доступа можно использовать для выполнения следующих задач:  
  
-   Обзор таблиц в каждой базе данных Access.  
  
-   Выберите объекты для преобразования и преобразовать объекты для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис. Дополнительные сведения см. в разделе [преобразование объектов базы данных Access](converting-access-database-objects-accesstosql.md).  
  
-   Выберите объекты для переноса данных и перенести данные из этих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [миграция данных Access в SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Создание и удаление доступа связи и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server или обозреватель метаданных базы данных Azure SQL  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных базы данных SQL Azure отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
SQL Server или обозреватель метаданных базы данных SQL Azure можно использовать для выбора преобразованных объектов базы данных Access и загрузки (синхронизации) этих объектов в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure.  
  
Дополнительные сведения см. в разделе [загрузка преобразовать объекты базы данных в SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозреватель метаданных находятся вкладки, которые описывают выбранного объекта. Например если выбрать таблицу в обозревателе метаданных доступ, отображаются четыре вкладки: **Таблица**, **сопоставление типов**, **свойства**, и **данных**. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, отображаются три вкладки: **Таблица**, **SQL**, и **данных**.  
  
Большинство параметров метаданных доступны только для чтения. Тем не менее можно изменить следующие метаданные:  
  
-   В обозревателе метаданных доступа можно изменить сопоставления типов. Не забудьте внести эти изменения, прежде чем создавать отчеты, или преобразовать схемы.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, его можно изменить свойства таблиц и индексов на **таблицы** вкладки. Внести эти изменения, прежде чем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [преобразование объектов базы данных Access](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA имеет две панели: панель инструментов проекта и инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панели инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, добавление доступа к файлам базы данных и подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Эти кнопки команды похожи на **файл** меню.  
  
#### <a name="the-migration-toolbar"></a>На панели инструментов миграции  
Панель инструментов миграции содержит следующие команды:  
  
|Кнопка|Компонент|  
|----------|------------|  
|**Преобразование, загрузка и миграция**|Преобразует базы данных Access, загружает преобразованные объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, и переносит данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, за один шаг.|  
|**Создание отчета**|Преобразует выбранная схема доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure, а затем создает отчет, показывающий, насколько успешно была преобразование.<br /><br />Эта команда доступна только в том случае, если выбраны объекты в обозревателе метаданных доступа.|  
|**Преобразовать схему**|Преобразует выбранная схема доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбраны объекты в обозревателе метаданных доступа.|  
|**Перенос данных**|Перенос данных из базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure. Перед выполнением этой команды, необходимо преобразовать схем доступа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы базы данных SQL Azure и затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбраны объекты в обозревателе метаданных доступа.|  
|**Остановить**|Останавливает текущий процесс, например преобразование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure.|  
  
### <a name="menus"></a>Меню  
SSMA содержит следующие меню:  
  
|Меню|Описание|  
|--------|---------------|  
|**Файл**|Содержит команды для мастера миграции, работе с проектами, добавления и удаления файлов баз данных Access и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure.|  
|**Изменить**|Содержит команды для поиска и работа с текстом на страницах сведения, такие как копирование [!INCLUDE[tsql](../../includes/tsql-md.md)] из области сведений SQL. Чтобы открыть **управление закладками** диалоговое окно, в меню "Правка" выберите Управление закладки. В диалоговом окне вы увидите список существующих закладок воспользуйтесь. Кнопки в правой части диалогового окна можно использовать для управления закладки.|  
|**Вид**|Содержит **обучающие ресурсы для синхронизации метаданных** команды. Это синхронизирует объекты между обозреватель метаданных доступа и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных базы данных SQL Azure. Также содержит команды для отображения и скрытия **вывода** и **список ошибок** областей и параметр **макеты** управлять с помощью макетов.|  
|**Инструменты**|Содержит команды для создания отчетов, экспортировать данные, перенести объекты и данные, связанные таблицы и предоставляет доступ к глобальным и параметры проекта диалоговых окон.|  
|**Справка**|Предоставляет доступ к справке SSMA и **о** диалоговое окно.|  
  
### <a name="output-pane-and-error-list-pane"></a>Области вывода и список ошибок  
**Представление** меню доступны команды для переключения видимости области вывода и список ошибок:  
  
-   На панели вывода показывает сообщения о состоянии из SSMA во время преобразования объекта, объект синхронизации и переноса данных.  
  
-   На панели списка ошибок отображаются ошибки, предупреждения и информационные сообщения, в списке, можно сортировать.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
