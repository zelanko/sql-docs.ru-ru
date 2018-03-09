---
title: "Компоненты потока ODBC | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf751f1e-2348-4a77-904c-bd92c0d7d0ae
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d2f92077fd1424827866820a0627ac62447e3f2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="odbc-flow-components"></a>Компоненты потока ODBC
  Этот раздел содержит описание основных понятий, необходимых для создания потока данных ODBC с использованием [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]  
  
 Соединитель для ODBC для [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] помогает разработчикам служб SSIS легко создавать пакеты, которые загружают и выгружают данные из поддерживающих ODBC баз данных.  
  
 Соединитель ODBC предназначен для достижения оптимальной производительности при загрузке или выгрузке данных из базы данных с поддержкой ODBC в контексте [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
## <a name="benefits"></a>Преимущества  
 Источник и назначение ODBC для [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] обеспечивают конкурентное превосходство для служб SSIS в проектах, связанных с загрузкой или выгрузкой данных из баз данных с поддержкой ODBC.  
  
 Источник и назначение ODBC обеспечивают высокопроизводительную интеграцию данных с базами данных с поддержкой ODBC. Оба компонента могут быть настроены для работы с привязками массива построчных параметров для высокопроизводительных поставщиков ODBC, которые поддерживают этот режим привязки, и привязками однострочных параметров для низкопроизводительных поставщиков ODBC.  
  
## <a name="getting-started-with-the-odbc-source-and-destination"></a>Приступая к работе с источником и назначением ODBC  
 Прежде чем появится возможность настройки пакетов, в которых используется [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], необходимо обеспечить соблюдение следующих требований.  
  
-   [ODBC-источник](../../integration-services/data-flow/odbc-source.md)  
  
-   [Назначение «ODBC»](../../integration-services/data-flow/odbc-destination.md)  
  
 Источник и назначение ODBC предоставляют простой способ выгрузки и загрузки данных, а также передачи данных из базы данных-источника с поддержкой ODBC в целевую базу данных с поддержкой ODBC.  
  
 Чтобы использовать источник или назначение для загрузки или выгрузки данных, откройте новые проект [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Затем перетащите источник или назначение в область конструктора [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
-   Компонент источника ODBC считывает данные из базы данных-источника с поддержкой ODBC.  
  
 Предусмотрена возможность подключить источник ODBC к любому назначению или преобразовать компонент, поддерживаемый службами SSIS.  
  
 **См. также**  
  
 ODBC-источник  
  
 Редактор источника «ODBC» (страница «Диспетчер соединений»)  
  
 Редактор источника «ODBC» (страница «Вывод ошибок»)  
  
-   Назначение ODBC загружает данные в базу данных с поддержкой ODBC. Назначение подключается к любому компоненту источника или преобразования, поддерживаемому службами SSIS.  
  
 **См. также**  
  
 Назначение ODBC  
  
 Редактор назначения «ODBC» (страница «Диспетчер соединений»)  
  
 Редактор назначения «ODBC» (страница «Вывод ошибок»)  
  
## <a name="operating-scenarios"></a>Сценарии работы  
 В этом разделе рассматриваются некоторые из основных способов использования компонентов источника и назначения ODBC.  
  
### <a name="bulk-copy-data-from-sql-server-tables-to-any-odbc-supported-database-table"></a>Массовое копирование данных из таблиц SQL Server в таблицу любой базы данных с поддержкой ODBC  
 Эти компоненты можно использовать для массового копирования данных из одной или нескольких таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в одну таблицу базы данных с поддержкой ODBC.  
  
 В следующем примере показано, как создать задачу «Поток данных служб SSIS», которая извлекает данные из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и загружает их в таблицу DB2.  
  
-   Создайте проект [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
-   Создайте диспетчер соединений OLE DB, который подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащей данные, предназначенные для копирования.  
  
-   Создайте диспетчер соединений ODBC, который использует локально установленный драйвер ODBC для DB2 с DSN, указывающий на локальную или удаленную базу данных DB2. Эта та база данных, в которую загружены данные из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Перетащите источник OLE DB в область конструктора, затем настройте источник для получения данных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и таблицы с данными, которые необходимо извлечь. Используйте созданный перед этим диспетчер соединений OLE DB.  
  
-   Перетащите назначение ODBC в область конструктора, подключите вывод источника к назначению ODBC, затем настройте назначение, чтобы загрузить данные в таблицу DB2 с данными, извлеченными из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Используйте созданный перед этим диспетчер соединений ODBC.  
  
### <a name="bulk-copy-data-from-odbc-supported-database-tables-to-any-sql-server-table"></a>Массовое копирование данных из таблиц базы данных с поддержкой ODBC в любую таблицу SQL Server  
 Компоненты можно использовать для массового копирования данных из одной или нескольких таблиц базы данных с поддержкой ODBC в одну таблицу базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 В следующем примере показано, как создать задачу «Поток данных SSIS», которая извлекает данные из таблицы базы данных Sybase и загружает их в таблицу базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Создайте проект [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
-   Создайте диспетчер соединений ODBC, который использует локально установленный драйвер ODBC для Sybase с DSN, указывающим на локальную или удаленную базу данных Sybase. Это база данных, из которой извлечены данные.  
  
-   Создайте диспетчер соединений OLE DB, который подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , куда должны быть загружены данные.  
  
-   Перетащите источник ODBC в область конструктора, затем настройте источник для получения данных из таблицы Sybase с данными, которые должны быть скопированы. Используйте созданный перед этим диспетчер соединений ODBC.  
  
-   Перетащите назначение «OLE DB» в область конструктора, подключите выход источника к назначению «OLE DB», затем настройте назначение для загрузки данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с данными, которые извлечены из базы данных Sybase. Используйте созданный перед этим диспетчер соединений OLE DB.  
  
## <a name="supported-data-types"></a>Поддерживаемые типы данных  
 Компоненты массовой загрузки ODBC для служб SSIS поддерживают все встроенные типы данных ODBC, включая поддержку больших объектов (CLOB и BLOB).  
  
Поддержка типов данных для расширяемых типов C, как описано в спецификации ODBC 3.8, отсутствует. В следующей таблице описано, какие типы данных служб SSIS используются для каждого из типов SQL ODBC. Разработчик служб SSIS может переопределить сопоставление, применяемое по умолчанию, и задать другой тип данных служб SSIS для столбцов ввода-вывода, не оказывая отрицательного воздействия на производительность требуемых преобразований данных.  
  
|Тип ODBC SQL|Тип данных служб SSIS|Комментарии|  
|-----------------|------------------|------------|  
|SQL_BIT|DT_BOOL||  
|SQL_TINYINT|DT_I1<br /><br />DT_UI1|Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.|  
|SQL_SMALLINT|DT_I2<br /><br />DT_UI2|Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.|  
|SQL_INTEGER|DT_I4<br /><br />DTUI4|Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.|  
|SQL_BIGINT|DT_I8<br /><br />DT_UI8|Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.|  
|SQL_DOUBLE|DT_R8|  
|SQL_FLOAT|DT_R8|  
|SQL_REAL|DT_R4|  
|SQL_NUMERIC (p,s)|DT_NUMERIC (p,s)|Числовой тип данных сопоставляется с DT_NUMERIC, если P больше или равно 38, а S больше или равно 0 и S меньше или равно P.|  
||DT_R8|Числовой тип данных сопоставляется с DT_R8, если соблюдается по крайней мере одно из следующих условий.<br /><br />Точность больше 38<br /><br />Масштаб меньше нуля<br /><br />Масштаб больше 38<br /><br />Масштаб больше точности|  
||DT_CY|Числовой тип данных сопоставляется с DT_CY, если он объявлен как тип данных money.|  
|SQL_DECIMAL (p,s)|DT_NUMERIC (p,s)|Тип данных decimal сопоставляется с DT_NUMERIC, если P больше или равно 38, а S больше или равно 0 и S меньше или равно P.|  
||DT_R8|Тип данных decimal сопоставляется с DT_R8, если соблюдается по крайней мере одно из следующих условий.<br /><br />Точность больше 38<br /><br />Масштаб меньше нуля<br /><br />Масштаб больше 38<br /><br />Масштаб больше точности|  
||DT_CY|Тип данных decimal сопоставляется с DT_CY, если он объявлен как тип данных money.|  
|SQL_DATE<br /><br />SQL_TYPE_DATE|DT_DBDATE|  
|SQL_TIME<br /><br />SQL_TYPE_TIME|DT_DBTIME|  
|SQL_TIMESTAMP<br /><br />SQL_TYPE_TIMESTAMP|DT_DBTIMESTAMP<br /><br />DT_DBTIMESTAMP2|Типы данных SQL_TIMESTAMP сопоставляются с DT_DBTIMESTAMP2, если масштаб больше 3. Во всех прочих случаях они сопоставляются с DT_DBTIMESTAMP.|  
|SQL_CHAR<br /><br />SQLVARCHAR|DT_STR<br /><br />DT_WSTR<br /><br />DT_TEXT<br /><br />DT_NTEXT|Тип DT_STR используется, если длина столбца меньше или равна 8000 и свойство **ExposeStringsAsUnicode** имеет значение false.<br /><br />Тип DT_WSTR используется, если длина столбца меньше или равна 8000 и свойство **ExposeStringsAsUnicode** имеет значение true.<br /><br />Тип DT_TEXT используется, если длина столбца больше 8000 и свойство **ExposeStringsAsUnicode** имеет значение false.<br /><br />Тип DT_NTEXT используется, если длина столбца больше 8000 и свойство **ExposeStringsAsUnicode** имеет значение true.|  
|SQL_LONGVARCHAR|DT_TEXT<br /><br />DT_NTEXT|Тип DT_NTEXT используется, если свойство **ExposeStringsAsUnicode** имеет значение true.|  
|SQL_WCHAR<br /><br />SQL_WVARCHAR|DT_WSTR<br /><br />DT_NTEXT|Тип DT_WSTR используется, если длина столбца меньше или равна 4000.<br /><br />Тип DT_NTEXT используется, если длина столбца больше 4000.|  
|SQL_WLONGVARCHAR|DT_NTEXT|  
|SQL_BINARY|DT_BYTE<br /><br />DT_IMAGE|Тип DT_BYTES используется, если длина столбца меньше или равна 8000.<br /><br />Тип DT_IMAGE используется, если длина столбца больше 8000.|  
|SQL_LONGVARBINARY|DT_IMAGE|  
|SQL_GUID|DT_GUID|  
|SQL_INTERVAL_YEAR<br /><br />SQL_INTERVAL_MONTH<br /><br />SQL_INTERVAL_DAY<br /><br />SQL_INTERVAL_HOUR<br /><br />SQL_INTERVAL_MINUTE<br /><br />SQL_INTERVAL_SECOND<br /><br />SQL_INTERVAL_YEAR_TO_MONTH<br /><br />SQL_INTERVAL_DAY_TO_HOUR<br /><br />SQL_INTERVAL_DAY_TO_MINUTE<br /><br />SQL_INTERVAL_DAY_TO_SECOND<br /><br />SQL_INTERVAL_HOUR_TO_MINUTE<br /><br />SQL_INTERVAL_HOUR_TO_SECOND<br /><br />SQL_INTERVAL_MINUTE_TO_SECOND|DT_WSTR|  
|Типы данных для конкретных поставщиков|DT_BYTES<br /><br />DT_IMAGE|Тип DT_BYTES используется, если длина столбца меньше или равна 8000.<br /><br />Тип DT_IMAGE используется, если длина столбца равна нулю или больше 8000.|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Источник «ODBC»](../../integration-services/data-flow/odbc-source.md)  
  
-   [Назначение ODBC](../../integration-services/data-flow/odbc-destination.md)  
  
 
