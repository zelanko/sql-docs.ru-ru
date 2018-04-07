---
title: С помощью нескольких активных результирующих наборов (MARS) | Документы Microsoft
description: Использование режима MARS
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, MARS
- MSOLEDBSQL, MARS
- data access [OLE DB Driver for SQL Server], MARS
- Multiple Active Result Sets
- OLE DB Driver for SQL Server, MARS
- MARS [SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 39950e9e23e0f77de977a0f0d276fdf8db6f1259
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="using-multiple-active-result-sets-mars"></a>Использование режима MARS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появилась поддержка множественных активных результирующих наборов (MARS) в приложения, использующие [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. В более ранних версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] приложения баз данных не могли поддерживать несколько активных инструкций во время соединения. При использовании результирующих наборов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], применяемых по умолчанию, приложение должно было обработать или отменить все результирующие наборы из одного пакета и только после этого приступать к обработке любого другого пакета данного соединения. В версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] был реализован новый атрибут соединения, который позволяет приложениям сохранять более одного ожидающего выполнения запроса в расчете на соединение и, в частности, иметь более одного применяемого по умолчанию активного результирующего набора в расчете на одно соединение.  
  
 Режим MARS упрощает проектирование приложений за счет использования следующих функций.  
  
-   У приложений может быть открыто несколько применяемых по умолчанию результирующих наборов; при этом приложения могут по очереди считывать из них данные.  
  
-   Когда применяемые по умолчанию результирующие наборы открыты, приложения могут выполнять другие инструкции (например: INSERT, UPDATE, DELETE и вызовы хранимых процедур).  
  
 При работе с приложениями, предусматривающими функционирование в режиме MARS, полезно руководствоваться следующими рекомендациями.  
  
-   Результирующие наборы по умолчанию следует использовать с имеющими небольшой период жизни или с короткими результирующими наборами, сформированными при помощи одной инструкции SQL (SELECT, DML with OUTPUT, RECEIVE, READ TEXT и т. д.).  
  
-   Серверные курсоры нужно использовать с имеющими более длительный период жизни или с более крупными результирующими наборами, сформированными при помощи одной инструкции SQL.  
  
-   Результаты нужно всегда прочитывать до конца на предмет наличия в них процедурных запросов, вне зависимости от того, возвращают ли они результаты, и на предмет наличия в них пакетов, возвращающих несколько результатов.  
  
-   По возможности для изменения свойств соединений и для управления транзакциями следует использовать не инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)], а вызовы API.  
  
-   При работе в режиме MARS в ситуациях, когда выполняются параллельные пакеты, ограниченные областью сеанса олицетворения не допускаются.  
  
> [!NOTE]  
>  По умолчанию функции режима MARS не активированы. Чтобы использовать режим MARS, при подключении к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с драйвер OLE DB для SQL Server, необходимо специально включить его в строке подключения. Дополнительные сведения см. в разделе драйвер OLE DB для SQL Server разделов, далее в этом разделе.  
  
 Драйвер OLE DB для SQL Server не ограничивает число активных инструкций в соединении.  
  
 Типичные приложения, которые обходятся одновременным выполнением не более чем одного пакета из нескольких инструкций или одной хранимой процедуры, лучше запускать в режиме MARS; при этом они не обязательно должны понимать, как именно реализован режим MARS. Однако приложения с более сложными требованиями должны принимать это во внимание.  
  
 Режим MARS дает возможность поочередно выполнять несколько запросов с использованием одного соединения. Иначе говоря, существует возможность выполнения пакета с одновременным выполнением других запросов. Впрочем, надо отметить, что режим MARS определяется в терминах чередования, а не в терминах параллельного выполнения.  
  
 Инфраструктура режима MARS предоставляет возможность поочередного выполнения нескольких пакетов, хотя выполнение может переключаться лишь в четко определенных пунктах. Кроме того, почти все инструкции должны выполняться атомарным образом внутри пакета. Инструкции, возвращающие строки клиенту, который иногда называют *точками выхода*, будет разрешено выполняться поочередно до завершения пока строки отправляются клиенту, например:  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Все иные инструкции, выполняемые как часть хранимой процедуры или пакета, должны выполняться до конца, и только после этого выполнение может быть передано другим запросам MARS.  
  
 Точный порядок чередования выполнения пакетов определяется рядом факторов, поэтому предугадать точную последовательность выполнения содержащих точки выхода команд из нескольких пакетов затруднительно. Необходимо проявлять осторожность, чтобы избегать нежелательных побочных эффектов, которые вызываются поочередным выполнением подобных сложных пакетов.  
  
 Вы сможете избежать проблем, если при управлении состоянием соединений (SET, USE) и транзакциями (BEGIN TRAN, COMMIT, ROLLBACK) будете использовать вызовы API, а не инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)], если не будете включать эти инструкции в пакеты из нескольких инструкций, также содержащие точки выхода, и если будете сериализовать выполнение таких пакетов посредством использования либо отмены всех результатов.  
  
> [!NOTE]  
>  Пакет хранимых процедур, начинающий ручную или неявную транзакцию с активированным режимом MARS, должен завершать транзакцию до выхода пакета. В противном случае по завершении выполнения пакета [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] осуществляет откат всех изменений, внесенных транзакцией. Такая транзакция управляется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как транзакция контекста пакета. Это новый тип транзакции, реализованный в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] с тем, чтобы существующие верно выполняемые хранимые процедуры можно было использовать в режиме MARS. Дополнительные сведения о транзакциях контекста пакета см. в разделе [инструкции транзакции &#40;Transact-SQL&#41;](../../../t-sql/statements/statements.md).  
  
 Пример использования режима MARS в ADO см. в разделе [с помощью ADO с драйвер OLE DB для SQL Server](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
## <a name="in-memory-oltp"></a>In-Memory OLTP  
 OLTP в памяти поддерживает режим MARS, с помощью запросов и скомпилированной хранимой процедуры. Режим MARS позволяет запрашивает данные из нескольких запросов без необходимости полностью получения каждого результирующего набора перед отправкой запроса для выборки строк из нового результирующего набора. Для того чтобы прочитать из нескольких открытые результирующие наборы, необходимо использовать режим MARS включен соединения.  
  
 Режим MARS отключен по умолчанию, необходимо явно включить его, добавив `MultipleActiveResultSets=True` строку подключения. Ниже приведен пример, как подключиться к экземпляру SQL Server и указать, что включен режим MARS:  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 Режим MARS с In-Memory OLTP, практически не таким же, как режим MARS в остальной части SQL engine. Ниже перечислены отличия при использовании режима MARS в таблицах, оптимизированных для памяти и в собственном коде хранимых процедур, скомпилированных.  
  
 **Режим MARS и таблицами, оптимизированными для памяти**  
  
 Ниже приведены различия между таблицами на диске и оптимизированных для памяти, при соединении с включенным с помощью режима MARS.  
  
-   Две инструкции может изменять данные в один и тот же целевой объект, но если они пытаются изменить ту же запись конфликт записи приведет к сбою операции создания. Тем не менее если обе операции изменения различных записей, будет выполнено операций.  
  
-   Каждая инструкция выполняется в режиме изоляции моментального СНИМКА, поэтому новые операции не может просматривать изменения, вносимые с существующие инструкции. Даже если в одной транзакции выполняются одновременно выполняемых инструкций SQL engine создает контекста пакета транзакций для каждой инструкции, которые изолированы друг от друга. Однако транзакции контекста пакета по-прежнему связаны друг, откат транзакции контекста пакета, один влияет на остальные в одном пакете.  
  
-   Операции DDL недопустимы в пользовательских транзакций, поэтому произойдет немедленно.  
  
 **Режим MARS и скомпилированных в собственном коде хранимых процедур**  
  
 Скомпилированные хранимые процедуры могут выполняться в подключения с включенным режимом MARS и может уступить выполнение другой инструкции только в том случае, когда встречается точка yield. Инструкция SELECT, которая является единственной инструкцией в скомпилированных в собственном коде хранимой процедуре, можно передать выполнение другой инструкции необходимы для точки yield. Если инструкция SELECT в процедуре, которую не окажет отсутствует, он будет выполняться до завершения прежде других инструкций.  
  
 **Операции режима MARS и In-memory OLTP**  
  
 Изменения, внесенные программой инструкций и блоки atomic, чередующиеся изолированы друг от друга. Например одной инструкции или блока atomic вносит некоторые изменения, а затем выдает выполнения в другой оператор, оператор new недоступен изменений, внесенных в первой инструкции. Кроме того при возобновлении выполнения первой инструкции не обнаруживает изменения, выполненные с любыми другими операторами. Операторы будут видеть только те изменения, которые являются завершения и фиксации до запуска инструкции.  
  
 Можно запустить новую транзакцию пользователя внутри текущей транзакции пользователя, используя инструкцию BEGIN TRANSACTION — это поддерживается только в режиме взаимодействия BEGIN TRANSACTION можно вызывать только из инструкции T-SQL и не из внутри скомпилированной в собственном коде хранимой процедура. Можно создать сохранения точки в транзакции, использующей SAVE TRANSACTION или вызов API для транзакции. Save(save_point_name) для отката до точки сохранения. Эта функция включена только из инструкций T-SQL и не из внутри скомпилированной хранимой процедуры.  
  
 **Режим MARS и индексов columnstore**  
  
 SQL Server (начиная с 2016) поддерживает режим MARS с индексами columnstore. SQL Server 2014 использует функцию MARS для соединения только для чтения с таблицами с индексом columnstore.    Но SQL Server 2014 не поддерживает функцию MARS для параллельного выполнения операций DML в таблице с индексом columnstore. В этом случае SQL Server завершить соединения и прервать транзакции.   SQL Server 2012 содержит индексы columnstore только для чтения и режим MARS не применяется к ним.  
  
## <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server  
 Драйвер OLE DB для SQL Server поддерживает режим MARS посредством добавления SSPROP_INIT_MARSCONNECTION свойство инициализации источника данных, которая реализована в наборе свойств dbpropset_sqlserverdbinit. Кроме того, ключевое слово строки новое соединение **MarsConn**, как были добавлены. Он принимает **true** или **false** значений; **false** значение по умолчанию.  
  
 Для свойства источника данных DBPROP_MULTIPLECONNECTIONS по умолчанию применяется значение VARIANT_TRUE. Это значит, что поставщик создаст несколько соединений для поддержки ряда параллельных объектов команд и наборов строк. Если включен режим MARS, драйвер OLE DB для SQL Server может поддерживать несколько объектов команд и наборов строк в одном соединении, поэтому MULTIPLE_CONNECTIONS по умолчанию задано значение VARIANT_FALSE.  
  
 Дополнительные сведения об улучшениях, появившихся в наборе свойств dbpropset_sqlserverdbinit см. в разделе [свойства инициализации и авторизации](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="ole-db-driver-for-sql-server-example"></a>Драйвер OLE DB, например SQL Server  
 В этом примере объект источника данных создается с помощью драйвера OLE DB для SQL Server и включен режим MARS, с помощью свойств DBPROPSET_SQLSERVERDBINIT перед созданием объекта session.  
  
```  
#include <msoledbsql.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  

  
## <a name="see-also"></a>См. также  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 
  
  
