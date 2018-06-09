---
title: Начало работы с SSMA для SAP ASE (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: eb7ace0b83cdb4277a742c9932430fedf7b3e532
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779280"
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>Начало работы с SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для SAP ASE позволяет быстро преобразовать схемы базы данных SAP адаптивной Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы базы данных SQL Azure, отправьте полученный схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure и переноса данных из SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или база данных Azure SQL.  
  
В этом разделе представлен процесс установки, а затем ознакомиться с SSMA пользовательского интерфейса.  
  
## <a name="installing-and-licensing-ssma"></a>Установка и лицензирование SSMA  
Чтобы использовать SSMA, сначала необходимо установить SSMA клиентской программы на компьютере, который доступен как исходного экземпляра служб SAP ASE и целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Использование миграции данных на сервере, необходимо установить пакет расширения и по крайней мере один из поставщиков SAP ASE (OLE DB или ADO.NET) на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти компоненты поддерживают перенос данных и эмуляции SAP ASE системных функций. Инструкции по установке см. в разделе [Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md).  
  
Для запуска SSMA нажмите кнопку **запустить**, пункты **все программы**, пункты  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Sybase**, а затем выберите  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Sybase**. При первом запуске SSMA, появляется диалоговое окно лицензирования. SSMA должен лицензии с помощью Windows Live ID, прежде чем использовать SSMA. Инструкции лицензирования входят в состав инструкции по установке в [Установка SSMA для клиента Sybase &#40;SybaseToSQL&#41; ](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) раздела.  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA для интерфейса пользователя SAP ASE  
После SSMA установлен и лицензирован, SSMA можно использовать для переноса базы данных SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Это позволяет ознакомиться с пользовательским интерфейсом SSMA перед запуском. На следующей диаграмме показан пользовательский интерфейс для SSMA, включая метаданные обозревателей, метаданных, панели инструментов, области вывода и панели «Список ошибок»:  
  
![SSMA для интерфейса SAP ASE пользователя](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA для интерфейса SAP ASE пользователя")  
  
Чтобы начать миграцию, сначала необходимо создать новый проект. Затем подключении к SAP ASE. После успешного подключения иерархии, SAP ASE баз данных будет отображаться в обозревателе метаданных Sybase. После этого можно объектов щелкните правой кнопкой мыши в обозревателе метаданных Sybase для выполнения задач, таких как создание отчеты, которые оценивают преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Можно также выполнить эти задачи с помощью панели инструментов и меню.  
  
Также необходимо подключиться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. После успешного подключения иерархии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных Azure SQL будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure. После преобразования схемы SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы базы данных SQL Azure, выберите преобразованные схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure и затем загружать эти схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.  
  
После загрузки схемы, преобразованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure, можно вернуться в обозреватель метаданных Sybase и перенести данные из базы данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или баз данных Azure SQL.  
  
Дополнительные сведения об этих задачах и порядок их выполнения см. в разделе [миграция SAP ASE баз данных в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md).  
  
В следующих разделах описаны возможности SSMA пользовательского интерфейса.  
  
### <a name="metadata-explorers"></a>Обозреватели метаданных  
SSMA содержит два обозреватели метаданных для просмотра и выполнения действий над SAP ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или баз данных Azure SQL.  
  
#### <a name="sybase-metadata-explorer"></a>Обозреватель метаданных Sybase  
Обозреватель метаданных Sybase показывает сведения о базах данных в экземпляре источника служб SAP ASE.  
  
С помощью обозревателя метаданных Sybase, можно выполнять следующие задачи:  
  
-   Обзор таблиц в каждой базе данных.  
  
-   Выберите объекты для преобразования, а затем преобразовать объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или синтаксис базы данных SQL Azure. Дополнительные сведения см. в разделе [преобразование объектов базы данных SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
-   Выберите объекты для переноса данных, а затем перенесите данные из таких объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Дополнительные сведения см. в разделе [переноса данных SAP ASE в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server или обозреватель метаданных SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или в обозревателе метаданных SQL Azure отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или база данных SQL Azure, SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
Можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure выберите преобразованные объекты базы данных SAP ASE и их загрузка (синхронизировать) этих объектов в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.  
  
Дополнительные сведения см. в разделе [загрузке преобразовать объекты базы данных в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозреватель метаданных являются вкладки, которые описывают выбранного объекта. Например, если выбрать таблицу в обозревателе метаданных Sybase, шесть вкладок: **таблицы**, **SQL**, **сопоставление типов**, **данные**,  **Свойства**, и **отчета**. **Отчетов** вкладка содержит сведения только после создания отчета, содержащего выбранного объекта. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, отображаются три вкладки: **таблицы**, **SQL**, и **данные**.  
  
Большинство параметров метаданные доступны только для чтения. Тем не менее можно изменить следующие метаданные:  
  
-   В обозревателе метаданных Sybase можно изменить процедуры и сопоставления типов. Внести эти изменения перед началом преобразования схемы.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, можно изменить [!INCLUDE[tsql](../../includes/tsql_md.md)] для хранимых процедур. Эти изменения перед их загрузкой схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Изменения, внесенные в обозревателе метаданных, отражаются в метаданные проекта, не в исходной или целевой базы данных.  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA имеет две панели: панель инструментов проекта и инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панели инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, подключении к SAP ASE и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Эти кнопки команды похожи на **файл** меню.  
  
#### <a name="the-migration-toolbar"></a>Панели инструментов миграции  
Панель инструментов миграции содержит следующие команды:  
  
|Кнопка|Компонент|  
|----------|------------|  
|**Создание отчета**|Преобразует выбранные объекты в SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксис, а затем создает отчет, которое показывает успешность преобразования.<br /><br />Эта команда доступна только в том случае, если выбранных объектов в обозревателе метаданных Sybase.|  
|**Преобразовать схему**|Преобразует выбранные объекты в SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбранных объектов в обозревателе метаданных Sybase.|  
|**Перенос данных**|Перемещает данные из базы данных SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Перед выполнением этой команды необходимо преобразовать схемы, SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы базы данных SQL Azure и затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.<br /><br />Эта команда доступна только в том случае, если выбранных объектов в обозревателе метаданных Sybase.|  
|**Остановить**|Останавливает текущий процесс, например преобразование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или синтаксис базы данных SQL Azure.|  
  
### <a name="menus"></a>Меню  
SSMA содержит следующие меню:  
  
|Меню|Описание|  
|--------|---------------|  
|**Файл**|Содержит команды для работы с проектами, подключении к SAP ASE и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.|  
|**Изменить**|Содержит команды для поиска и работа с текстом в страницы сведений, например для копирования [!INCLUDE[tsql](../../includes/tsql_md.md)] из области сведений SQL. Также содержит **управление закладки** вариант, где можно просмотреть список существующих закладок. Кнопки в правой части диалогового окна можно использовать для управления закладки.|  
|**Вид**|Содержит **синхронизировать метаданные обозреватели** команды. Это синхронизирует объектов между Sybase в обозревателе метаданных и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure. Также содержит команды для отображения и скрытия **вывода** и **список ошибок** области и в качестве параметра **макеты** управление макетами.|  
|**Инструменты**|Содержит команды для создания отчетов, экспорт данных и миграция объектов и данных. Также предоставляет доступ к **глобальные параметры** и **параметры проекта** диалоговым окнам.|  
|**Тест-инженер**|Содержит команды для создания тестовых случаев, просматривать результаты тестов и команды для управления резервным копированием базы данных.|  
|**Справка**|Предоставляет доступ к справке SSMA и **о** диалоговое окно.|  
  
### <a name="output-pane-and-error-list-pane"></a>Область вывода и «список ошибок»  
**Представление** предоставляет меню команд для переключения видимости области вывода и области списка ошибок:  
  
-   Область вывода показывает сообщения о состоянии из SSMA во время преобразования объекта синхронизации объектов и переноса данных.  
  
-   В области списка ошибок отображаются ошибки, предупреждения и информационные сообщения в списке, можно выполнить сортировку.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных SAP ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Справочник по пользовательскому интерфейсу &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
