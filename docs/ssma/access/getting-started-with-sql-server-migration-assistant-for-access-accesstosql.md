---
title: Приступая к работе с SQL Server Migration Assistant для Access | Документы Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 2c9195abaee31950fae9d26eb64f01d38ffa0447
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773970"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Приступая к работе с SQL Server Migration Assistant для Access (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для доступа позволяет быстро преобразовывать объекты базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных SQL Azure, передать полученные объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure, и перенести данные с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. При необходимости можно также связать доступа к таблицам для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц базы данных SQL Azure, чтобы продолжить использовать существующие приложения Access переднего плана с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.  
  
Содержит вводные сведения в процессе установки, в этом разделе для ознакомления с SSMA пользовательского интерфейса.  
  
## <a name="installing-ssma"></a>Установка SSMA  
Чтобы использовать SSMA, сначала необходимо установить SSMA клиентской программы на компьютере доступ обеих баз данных, которые требуется перенести и целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. Инструкции по установке см. в разделе [Установка SQL Server Migration Assistant для Access &#40;AccessToSQL&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Для запуска SSMA нажмите кнопку **запустить**, пункты **все программы**, пункты **SQL Server Migration Assistant для Access**и выберите **SQL Server Migration Assistant для Access**.  
  
## <a name="using-ssma"></a>С помощью SSMA  
После установки SSMA, полезно ознакомиться с пользовательским интерфейсом SSMA перед использованием средства для переноса базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. Пользовательский интерфейс SSMA, включая метаданные обозревателей, метаданных, панели инструментов, области вывода и панели «Список ошибок» показаны на следующей схеме:  
  
![SSMA для графического пользовательского интерфейса доступа](../../ssma/access/media/ssmaforaccessgui.gif "SSMA для Access графического интерфейса пользователя")  
  
Чтобы начать миграцию, создайте новый проект и затем добавьте доступ обозреватель метаданных базы данных Access. Затем щелкнуть правой кнопкой мыши объектов в обозревателе метаданных доступ для выполнения задач, таких как:
- Экспорт инвентаризацию объектов базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.
- Создание отчетов, которые оценивают преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.
- Преобразование схем доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы базы данных SQL Azure.

Эти задачи можно также выполнить с помощью панели инструментов и меню.  
  
Также необходимо подключиться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. После успешного подключения иерархии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных отображается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных. После преобразования схем доступа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы, можно выбрать преобразованные схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных и затем загружать эти схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Если выбрана база данных SQL Azure из миграции в раскрывающемся списке в диалоговом окне нового проекта, необходимо подключиться к базе данных SQL Azure. После успешного подключения иерархия баз данных в базе данных SQL Azure отображается в обозревателе метаданных базы данных SQL Azure. После преобразования схемы доступа к схемы базы данных SQL Azure, можно выбрать преобразованные схемы в обозревателе метаданных базы данных SQL Azure и затем загружать эти схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
После загрузки схемы, преобразованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure, можно вернуться в обозреватель метаданных доступа и перенести данные из базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или баз данных в базе данных SQL Azure. При необходимости можно также связать доступа к таблицам для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц базы данных SQL Azure.  
  
Дополнительные сведения об этих задачах и порядок их выполнения см. в следующих разделах:  
  
-   [Подготовка к миграции базы данных Access](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
-   [Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
-   [Связывание приложения Access в SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  
В следующих разделах описаны возможности SSMA пользовательского интерфейса.  
  
### <a name="metadata-explorers"></a>Обозреватели метаданных  
SSMA содержит два метаданных обозревателей, которые можно использовать для просмотра и выполнять действия на доступ и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или баз данных в базе данных SQL Azure.  
  
#### <a name="access-metadata-explorer"></a>Доступ к обозревателю метаданных  
Обозреватель метаданных доступ показывает сведения о базах данных Access, которые были добавлены в проект. При добавлении базы данных Access, SSMA извлекает метаданные об этой базе данных метаданных, доступных в обозревателе метаданных доступа.  
  
Обозреватель метаданных доступа можно использовать для выполнения следующих задач:  
  
-   Обзор таблиц в каждой базе данных Access.  
  
-   Выберите объекты для преобразования и преобразования объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксиса. Дополнительные сведения см. в разделе [преобразование объектов базы данных Access](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c).  
  
-   Выберите объекты для переноса данных и переноса данных из этих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [перенос данных Access в SQL Server](http://msdn.microsoft.com/f3b18af7-1af0-499d-a00d-a0af94895625).  
  
-   Создание и удаление доступа связи и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] таблицы.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server или в обозревателе метаданных базы данных Azure SQL  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или в обозревателе метаданных базы данных SQL Azure отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или база данных SQL Azure, SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
SQL Server или SQL Azure в обозревателе метаданных базы данных можно использовать для выбора преобразованные объекты базы данных Access и загрузить (синхронизировать) этих объектов в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.  
  
Дополнительные сведения см. в разделе [загрузке преобразовать объекты базы данных в SQL Server](http://msdn.microsoft.com/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозреватель метаданных являются вкладки, которые описывают выбранного объекта. Например, при выборе таблицы в обозревателе метаданных доступ четырех вкладок: **таблицы**, **сопоставление типов**, **свойства**, и **данные**. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных отображаются три вкладки: **таблицы**, **SQL**, и **данные**.  
  
Большинство параметров метаданные доступны только для чтения. Тем не менее можно изменить следующие метаданные:  
  
-   В обозревателе метаданных доступа может изменять сопоставления типов. Убедитесь, что эти изменения, прежде чем создавать отчеты или преобразование схемы.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных свойства таблиц и индексов можно изменить на **таблицы** вкладки. Эти изменения перед их загрузкой схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [преобразование объектов базы данных Access](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c).  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA имеет две панели: панель инструментов проекта и инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панели инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, добавление доступа к файлам базы данных и подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. Эти кнопки команды похожи на **файл** меню.  
  
#### <a name="the-migration-toolbar"></a>Панели инструментов миграции  
Панель инструментов миграции содержит следующие команды:  
  
|Кнопка|Компонент|  
|----------|------------|  
|**Преобразование, загрузка и миграция**|Преобразует базы данных Access, загружает объекты, преобразованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure, и переносит данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure за один шаг.|  
|**Создание отчета**|Преобразует выбранная схема доступа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или синтаксис базу данных SQL Azure и создает отчет, которое показывает успешность преобразования.<br /><br />Эта команда доступна только в том случае, если выбранных объектов в обозревателе метаданных доступа.|  
|**Преобразовать схему**|Преобразует выбранная схема доступа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы базы данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбранных объектов в обозревателе метаданных доступа.|  
|**Перенос данных**|Перемещает данные из базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. Перед выполнением этой команды необходимо преобразовать схемы, доступ [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы базы данных SQL Azure и затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбранных объектов в обозревателе метаданных доступа.|  
|**Остановить**|Останавливает текущий процесс, например преобразование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или синтаксис базу данных SQL Azure.|  
  
### <a name="menus"></a>Меню  
SSMA содержит следующие меню:  
  
|Меню|Описание|  
|--------|---------------|  
|**Файл**|Содержит команды для мастера миграции, работа с проектами, добавления и удаления файлов баз данных Access и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.|  
|**Изменить**|Содержит команды для поиска и работа с текстом в страницы сведений, например для копирования [!INCLUDE[tsql](../../includes/tsql_md.md)] из области сведений SQL. Чтобы открыть **управление закладки** диалоговое окно, в меню Правка выберите Управление закладки. В диалоговом окне вы увидите список существующих закладок. Кнопки в правой части диалогового окна можно использовать для управления закладки.|  
|**Вид**|Содержит **синхронизировать метаданные обозреватели** команды. Это синхронизирует объектов между обозреватель метаданных доступа и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных базы данных SQL Azure. Также содержит команды для отображения и скрытия **вывода** и **список ошибок** области и в качестве параметра **макеты** для управления с макетами.|  
|**Инструменты**|Содержит команды для создания отчетов, экспорт данных, перенести объекты и данные, связанные таблицы и предоставляет доступ к глобальным и параметры проекта диалоговых окон.|  
|**Справка**|Предоставляет доступ к справке SSMA и **о** диалоговое окно.|  
  
### <a name="output-pane-and-error-list-pane"></a>Область вывода и «список ошибок»  
**Представление** предоставляет меню команд для переключения видимости области вывода и области списка ошибок:  
  
-   Область вывода показывает сообщения о состоянии из SSMA во время преобразования объекта синхронизации объектов и переноса данных.  
  
-   В области списка ошибок отображаются ошибки, предупреждения и информационные сообщения в списке, можно выполнить сортировку.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
