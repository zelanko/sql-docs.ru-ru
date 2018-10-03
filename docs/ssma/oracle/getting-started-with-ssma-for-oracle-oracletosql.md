---
title: Начало работы с SSMA для Oracle (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 80fc86c4b3d9385dc056b0c0ea9633f9f5f26675
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782072"
---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>Начало работы с SSMA для Oracle (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для Oracle позволяет быстро, преобразование схем баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы, отправьте полученный схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перенос данных из Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
В этом разделе представлен процесс установки, а затем ознакомиться с пользовательским интерфейсом SSMA.  
  
## <a name="installing-ssma"></a>Установка SSMA  
Чтобы использовать SSMA, сначала необходимо установить SSMA клиентскую программу на компьютере с доступом к базе данных Oracle источника и целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем необходимо установить пакет расширения и по крайней мере одного из поставщиков Oracle (OLE DB или [!INCLUDE[vstecado](../../includes/vstecado_md.md)]) на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти компоненты поддерживают перенос данных и эмуляции Oracle системных функций. Инструкции по установке см. в разделе [Установка SSMA для Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md).  
  
Для запуска SSMA, нажмите кнопку **запустить**, пункты **все программы**, пункты  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant для Oracle**, а затем нажмите кнопку  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant для Oracle**.  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA для интерфейса пользователя Oracle  
После установки SSMA SSMA можно использовать для переноса баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Он позволяет ознакомиться с пользовательским интерфейсом SSMA, прежде чем начать. В примере ниже показан пользовательский интерфейс для SSMA, включая обучающие ресурсы для метаданных, метаданные, панелей инструментов, область вывода и область списка ошибок:  
  
![SSMA для интерфейса пользователя Oracle](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA для интерфейса пользователя Oracle")  
  
Чтобы начать миграцию, необходимо сначала создать новый проект. Затем вы подключитесь к базе данных Oracle. После успешного подключения схем Oracle будет отображаться в обозревателе метаданных Oracle. После этого можно объектов щелкните правой кнопкой мыши в обозревателе метаданных Oracle для выполнения задач, таких как создание отчетов, которые оценивают преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти задачи также можно выполнить с помощью панели инструментов и меню.  
  
Также необходимо подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После успешного подключения иерархию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. После преобразования схем Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы, выберите преобразованный схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, а затем синхронизировать схемы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
После синхронизации преобразованный схемы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно вернуться в обозреватель метаданных Oracle и переноса данных из схем Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных.  
  
Дополнительные сведения об этих задачах и порядок их выполнения см. в разделе [Миграция баз данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md).  
  
Ниже описаны возможности пользовательского интерфейса SSMA.  
  
### <a name="metadata-explorers"></a>Обучающие ресурсы для метаданных  
SSMA содержит два проводников метаданных для просмотра и выполнения действий в Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных.  
  
#### <a name="oracle-metadata-explorer"></a>Обозреватель метаданных Oracle  
Обозреватель метаданных Oracle показывает сведения о схемах Oracle. С помощью обозревателя метаданных Oracle, можно выполнять следующие задачи:  
  
-   Просмотрите объекты в каждой схеме.  
  
-   Выберите объекты для преобразования, а затем преобразовать объекты для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис. Дополнительные сведения см. в разделе [преобразование схем Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
-   Выбрать таблицы для переноса данных, а затем перенесите данные из этих таблиц в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [миграция данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>Обозреватель метаданных SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Обозреватель метаданных отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA извлекает метаданные об этом экземпляре и сохраняет его в файле проекта.  
  
Можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, чтобы выбрать преобразованных объектов базы данных Oracle, а затем синхронизировать их с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Дополнительные сведения см. в разделе [загрузка преобразовать объекты базы данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
### <a name="metadata"></a>Метаданные  
Справа от каждого обозреватель метаданных находятся вкладки, которые описывают выбранного объекта. Например, если выбрать таблицу в обозревателе метаданных Oracle, шесть вкладок появится: **таблицы**, **SQL**, **сопоставления типов, отчет**, **свойства**, и **данных**. **Отчетов** вкладка содержит сведения только после создания отчета, содержащий выбранный объект. Если выбрать таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, которые будут отображаться три вкладки: **таблицы**, **SQL**, и **данных**.  
  
Большинство параметров метаданных доступны только для чтения. Тем не менее можно изменить следующие метаданные:  
  
-   В обозревателе метаданных Oracle можно изменить процедуры и сопоставления типов. Чтобы преобразовать измененный процедуры и сопоставления типов, внесите изменения, перед началом преобразования схемы.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных можно изменить [!INCLUDE[tsql](../../includes/tsql-md.md)] для хранимых процедур. Чтобы увидеть эти изменения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], внести эти изменения, прежде чем загрузить схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Изменения, внесенные в обозревателе метаданных, отражаются в метаданные проекта, не в исходной или целевой базы данных.  
  
### <a name="toolbars"></a>Панели инструментов  
SSMA имеет две панели: панель инструментов проекта и инструментов миграции.  
  
#### <a name="the-project-toolbar"></a>Панели инструментов проекта  
Панель инструментов проекта содержит кнопки для работы с проектами, подключение к базе данных Oracle и подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти кнопки команды похожи на **файл** меню.  
  
#### <a name="migration-toolbar"></a>Панель инструментов миграции  
В следующей таблице показаны миграции команды панели инструментов:  
  
|Кнопка|Компонент|  
|------|--------|  
|**Создание отчета**|Преобразует выбранных объектов Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, а затем создает отчет, показывающий, насколько успешно была преобразование.<br /><br />Эта команда отключает в том случае, если выбраны объекты в обозревателе метаданных Oracle.|  
|**Преобразовать схему**|Преобразует выбранных объектов Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов.<br /><br />Эта команда отключает в том случае, если выбраны объекты в обозревателе метаданных Oracle.|  
|**Перенос данных**|Перенос данных из базы данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перед выполнением этой команды, необходимо преобразовать схем Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схем, а затем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Эта команда отключает в том случае, если выбраны объекты в обозревателе метаданных Oracle.|  
|**Остановить**|Останавливает текущий процесс.|  
  
### <a name="menus"></a>Меню  
В следующей таблице показаны SSMA меню.  
  
|Меню|Описание|  
|----|-----------|  
|**Файл**|Содержит команды для работы с проектами, подключение к базе данных Oracle и подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Изменить**|Содержит команды для поиска и работа с текстом на страницах сведения, такие как копирование [!INCLUDE[tsql](../../includes/tsql-md.md)] из области сведений SQL. Также содержит **управление закладками** параметр, где будут иметь возможность просмотреть список существующих закладок воспользуйтесь. Кнопки в правой части диалогового окна можно использовать для управления закладки.|  
|**Вид**|Содержит **обучающие ресурсы для синхронизации метаданных** команды. Которая позволяет синхронизировать объекты между обозреватель метаданных Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. Также содержит команды для отображения и скрытия **вывода** и **список ошибок** областей и параметр **макеты** для управления макетов.|  
|**Инструменты**|Команды для создания отчетов и перенести объекты и данные. Также предоставляет доступ к **глобальные параметры** и **параметры проекта** диалоговым окнам.|  
|**Тест-инженер**|Команды для создания и работы с тестовыми случаями, репозитория и системы управления резервным копированием.|  
|**Справка**|Предоставляет доступ к справке SSMA и **о** диалоговое окно.|  
  
### <a name="output-pane-and-error-list-pane"></a>Область вывода и область списка ошибок  
**Представление** меню доступны команды для переключения видимости области вывода и список ошибок:  
  
-   На панели вывода показывает сообщения о состоянии из SSMA во время преобразования объекта, объект синхронизации и переноса данных.  
  
-   На панели списка ошибок отображаются ошибки, предупреждения и информационные сообщения в список поддерживает сортировку.  
  
## <a name="see-also"></a>См. также  
[Миграция данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[Справочник по пользовательскому интерфейсу &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
