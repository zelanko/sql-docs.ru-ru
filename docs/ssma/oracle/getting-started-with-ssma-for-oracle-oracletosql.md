---
title: Начало работы с SSMA для Oracle (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: abf70f96f33a0f411fbad546dc8ad68eb87ae8c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>Начало работы с SSMA для Oracle (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для Oracle позволяет быстро преобразование схем баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схем, отправьте полученный схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и перенос данных из Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
В этом разделе представлен процесс установки, а затем ознакомиться с SSMA пользовательского интерфейса.  
  
## <a name="installing-ssma"></a>Установка SSMA  
Чтобы использовать SSMA, сначала необходимо установить SSMA клиентской программы на компьютере, который можно получить доступ к исходной базе данных Oracle и целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Затем необходимо установить пакет расширения и по крайней мере одного из поставщиков Oracle (OLE DB или [!INCLUDE[vstecado](../../includes/vstecado_md.md)]) на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти компоненты поддерживают перенос данных и эмуляции Oracle системных функций. Инструкции по установке см. в разделе [Установка SSMA для Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md).  
  
Для запуска SSMA нажмите кнопку **запустить**, пункты **все программы**, пункты  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Oracle**, а затем нажмите кнопку  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Oracle**.  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA для интерфейса пользователя Oracle  
После установки SSMA SSMA можно использовать для переноса баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Это позволяет ознакомиться с пользовательским интерфейсом SSMA перед запуском. На следующей диаграмме показан пользовательский интерфейс для SSMA, включая метаданные обозревателей, метаданных, панели инструментов, области вывода и панели «Список ошибок»:  
  
![SSMA для интерфейса пользователя Oracle](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA для интерфейса пользователя Oracle")  
  
Чтобы начать миграцию, сначала необходимо создать новый проект. Затем подключитесь к базе данных Oracle. После успешного подключения Oracle схемы будет отображаться в обозревателе метаданных Oracle. После этого можно объектов щелкните правой кнопкой мыши в обозревателе метаданных Oracle для выполнения задач, таких как создавать отчеты, которые оценивают преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти задачи можно также выполнить с помощью панели инструментов и меню.  
  
Также необходимо подключиться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. После успешного подключения иерархии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных. После преобразования схемы Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы, выберите преобразованные схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, а затем выполните синхронизацию схемы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
После синхронизации преобразованные схемы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно вернуться в обозреватель метаданных Oracle и переноса данных из Oracle схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных.  
  
Дополнительные сведения об этих задачах и порядок их выполнения см. в разделе [Миграция баз данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md).  
  
В следующих разделах описаны возможности SSMA пользовательского интерфейса.  
  
### <a name="metadata-explorers"></a>Обозреватели метаданных  
SSMA содержит два обозреватели метаданных для просмотра и выполнения действий над Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных.  
  
#### <a name="oracle-metadata-explorer"></a>Обозреватель метаданных Oracle  
Обозреватель метаданных Oracle показывает сведения о схемах Oracle. С помощью обозревателя метаданных Oracle, можно выполнять следующие задачи:  
  
-   Просматривать объекты в каждой схеме.  
  
-   Выберите объекты для преобразования, а затем преобразовать объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксиса. Дополнительные сведения см. в разделе [преобразование схемы Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
-   Выберите таблицы для переноса данных, а затем перенести данные из этих таблиц в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [переноса данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>Обозреватель метаданных SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Обозреватель метаданных отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
Можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных для выбора преобразованные объекты базы данных Oracle, а затем синхронизировать их с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Дополнительные сведения см. в разделе [загрузке преобразовать объекты базы данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозреватель метаданных являются вкладки, которые описывают выбранного объекта. Например, если выбрать таблицу в обозревателе метаданных Oracle, шесть вкладок появится: **таблицы**, **SQL**, **сопоставление типов, отчет**, **свойства**, и **данные**. **Отчетов** вкладка содержит сведения только после создания отчета, содержащий выбранный объект. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных, которые будут отображаться три вкладки: **таблицы**, **SQL**, и **данные**.  
  
Большинство параметров метаданные доступны только для чтения. Тем не менее можно изменить следующие метаданные:  
  
-   В обозревателе метаданных Oracle можно изменить процедуры и сопоставления типов. Чтобы преобразовать измененную процедуры и сопоставления типов, внесите изменения, перед началом преобразования схемы.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных можно изменить [!INCLUDE[tsql](../../includes/tsql_md.md)] для хранимых процедур. Чтобы увидеть эти изменения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], эти изменения перед их загрузкой схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Изменения, внесенные в обозревателе метаданных, отражаются в метаданные проекта, не в исходной или целевой базы данных.  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA имеет две панели: панель инструментов проекта и инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панели инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, подключение к базе данных Oracle и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти кнопки команды похожи на **файл** меню.  
  
#### <a name="migration-toolbar"></a>Панель инструментов миграции  
В следующей таблице показаны миграции команды панели инструментов:  
  
|Кнопка|Функция|  
|------|--------|  
|**Создание отчета**|Преобразует выделенных объектов Oracle по [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксис, а затем создает отчет, которое показывает успешность преобразования.<br /><br />Эта команда недоступна, если только выбранных объектов в обозревателе метаданных Oracle.|  
|**Преобразовать схему**|Преобразует выделенных объектов Oracle по [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] объектов.<br /><br />Эта команда недоступна, если только выбранных объектов в обозревателе метаданных Oracle.|  
|**Перенос данных**|Миграция данных из базы данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Перед выполнением этой команды необходимо преобразовать схемы Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схем, а затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br />Эта команда недоступна, если только выбранных объектов в обозревателе метаданных Oracle.|  
|**Остановить**|Останавливает текущий процесс.|  
  
### <a name="menus"></a>Меню  
В следующей таблице показаны SSMA меню.  
  
|Меню|Описание|  
|----|-----------|  
|**Файл**|Содержит команды для работы с проектами, подключение к базе данных Oracle и подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**Правка**|Содержит команды для поиска и работа с текстом в страницы сведений, например для копирования [!INCLUDE[tsql](../../includes/tsql_md.md)] из области сведений SQL. Также содержит **управление закладки** вариант, где вы сможете для просмотра списка существующих закладок. Кнопки в правой части диалогового окна можно использовать для управления закладки.|  
|**Вид**|Содержит **синхронизировать метаданные обозреватели** команды. Который синхронизирует объектов между Oracle в обозревателе метаданных и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозреватель метаданных. Также содержит команды для отображения и скрытия **вывода** и **список ошибок** области и в качестве параметра **макеты** управление макетами.|  
|**Инструменты**|Содержит команды для создания отчетов и перенести объекты и данные. Также предоставляет доступ к **глобальные параметры** и **параметры проекта** диалоговым окнам.|  
|**Тест-инженер**|Содержит команды для создания и работы с тестовыми случаями, репозитория и системы управления резервным копированием.|  
|**Справка**|Предоставляет доступ к справке SSMA и **о** диалоговое окно.|  
  
### <a name="output-pane-and-error-list-pane"></a>Область вывода и панели «Список ошибок»  
**Представление** предоставляет меню команд для переключения видимости области вывода и области списка ошибок:  
  
-   Область вывода показывает сообщения о состоянии из SSMA во время преобразования объекта синхронизации объектов и переноса данных.  
  
-   В области списка ошибок отображаются ошибки, предупреждения и информационные сообщения в сортируемый список.  
  
## <a name="see-also"></a>См. также  
[Перенос данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[Справочник по пользовательскому интерфейсу &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
