---
title: Использование режима MARS | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, MARS
- SQLNCLI, MARS
- data access [SQL Server Native Client], MARS
- Multiple Active Result Sets
- SQL Server Native Client, MARS
- MARS [SQL Server]
- SQL Server Native Client ODBC driver, MARS
ms.assetid: ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fdf953bd5cb1835b2d2f6cc0e868a3687e53e852
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303226"
---
# <a name="using-multiple-active-result-sets-mars"></a>Использование режима MARS

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] была предусмотрена возможность работы с несколькими активными результирующими наборами (режим MARS) в приложениях, которые обращаются к компоненту [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. В более ранних версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] приложения баз данных не могли поддерживать несколько активных инструкций во время соединения. При использовании результирующих наборов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], применяемых по умолчанию, приложение должно было обработать или отменить все результирующие наборы из одного пакета и только после этого приступать к обработке любого другого пакета данного соединения. В версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] был реализован новый атрибут соединения, который позволяет приложениям сохранять более одного ожидающего выполнения запроса в расчете на соединение и, в частности, иметь более одного применяемого по умолчанию активного результирующего набора в расчете на одно соединение.  
  
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
> По умолчанию функция MARS не включена драйвером. Чтобы использовать режим MARS при [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] соединении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с с собственным клиентом, необходимо явным образом включить режим MARS в строке подключения. Однако некоторые приложения по умолчанию могут включить режим MARS, если приложение обнаружит, что драйвер поддерживает режим MARS. Для этих приложений при необходимости можно отключить режим MARS в строке подключения. Дополнительные сведения см. в подразделах «Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]» и «Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]» далее в этом разделе.

 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не ограничивает число активных инструкций в соединении.  
  
 В обычных приложениях, которые не требуют одновременного выполнения нескольких инструкций или хранимых процедур с несколькими инструкциями, будет выгоден режим MARS без необходимости понимания реализации режима MARS. Однако приложения с более сложными требованиями должны принимать это во внимание.  
  
 Режим MARS дает возможность поочередно выполнять несколько запросов с использованием одного соединения. Иначе говоря, существует возможность выполнения пакета с одновременным выполнением других запросов. Впрочем, надо отметить, что режим MARS определяется в терминах чередования, а не в терминах параллельного выполнения.  
  
 Инфраструктура режима MARS предоставляет возможность поочередного выполнения нескольких пакетов, хотя выполнение может переключаться лишь в четко определенных пунктах. Кроме того, почти все инструкции должны выполняться атомарным образом внутри пакета. Инструкции, которые возвращают строки клиенту, которые иногда называют *точками*получения, могут чередовать выполнение до завершения, пока строки отправляются клиенту, например:  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Все иные инструкции, выполняемые как часть хранимой процедуры или пакета, должны выполняться до конца, и только после этого выполнение может быть передано другим запросам MARS.  
  
 Точный порядок чередования выполнения пакетов определяется рядом факторов, поэтому предугадать точную последовательность выполнения содержащих точки выхода команд из нескольких пакетов затруднительно. Необходимо проявлять осторожность, чтобы избегать нежелательных побочных эффектов, которые вызываются поочередным выполнением подобных сложных пакетов.  
  
 Вы сможете избежать проблем, если при управлении состоянием соединений (SET, USE) и транзакциями (BEGIN TRAN, COMMIT, ROLLBACK) будете использовать вызовы API, а не инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)], если не будете включать эти инструкции в пакеты из нескольких инструкций, также содержащие точки выхода, и если будете сериализовать выполнение таких пакетов посредством использования либо отмены всех результатов.  
  
> [!NOTE]  
>  Пакет хранимых процедур, начинающий ручную или неявную транзакцию с активированным режимом MARS, должен завершать транзакцию до выхода пакета. В противном случае по завершении выполнения пакета [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] осуществляет откат всех изменений, внесенных транзакцией. Такая транзакция управляется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как транзакция контекста пакета. Это новый тип транзакции, реализованный в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] с тем, чтобы существующие верно выполняемые хранимые процедуры можно было использовать в режиме MARS. Дополнительные сведения о транзакциях контекста пакета см. в статье [Инструкции Transact-SQL](~/t-sql/statements/statements.md).  
  
 Пример использования режима MARS из ADO см. в разделе [Использование ADO с SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="in-memory-oltp"></a>Выполняющаяся в памяти OLTP  
 Выполняющаяся в памяти OLTP поддерживает режим MARS с помощью запросов и скомпилированных в собственном коде хранимых процедур. Режим MARS позволяет запрашивать данные из нескольких запросов без необходимости полного извлечения каждого результирующего набора перед отправкой запроса для выборки строк из нового результирующего набора. Для успешного чтения из нескольких открытых результирующих наборов необходимо использовать подключение с поддержкой режима MARS.  
  
 Режим MARS отключен по умолчанию, поэтому его необходимо явно включить, добавив `MultipleActiveResultSets=True` в строку подключения. В следующем примере демонстрируется, как подключиться к экземпляру SQL Server, а также как указать, что режим MARS включен.  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 Режим MARS с выполняющейся в памяти OLTP, по сути, аналогичен режиму MARS в оставшейся части ядра SQL. Ниже перечислены различия при использовании режима MARS для таблиц, оптимизированных для памяти, и хранимых процедур, скомпилированных в собственном коде.  
  
 **Режим MARS и таблицы, оптимизированные для памяти**  
  
 Ниже приведены различия между таблицами, оптимизированными для дисков и памяти, при использовании подключения с включенным режимом MARS.  
  
-   Две инструкции могут изменять данные в том же целевом объекте, но если они обе пытаются изменить одну и ту же запись, конфликт между двумя операциями приведет к сбою новой операции. Тем не менее если обе операции изменяют разные записи, операции будут выполнены.  
  
-   Каждая инструкция выполняется с изоляцией моментального снимка, поэтому новые операции не могут видеть изменения, внесенные существующими инструкциями. Даже если параллельные инструкции выполняются в рамках одной транзакции, ядро SQL создает транзакции контекста пакета для каждой инструкции, изолированной друг от друга. Тем не менее транзакции контекста пакета по-прежнему связаны друг с другом, поэтому откат одной транзакции влияет на другие, которые находятся в том же пакете.  
  
-   Операции DDL запрещены в пользовательских транзакциях, поэтому они будут немедленно завершаться сбоем.  
  
 **Режим MARS и скомпилированные в собственном коде хранимые процедуры**  
  
 Скомпилированные в собственном коде хранимые процедуры могут работать в подключениях с включенным режимом MARS и передавать выполнение другой инструкции только при обнаружении точки передачи. Для точки передачи требуется инструкция SELECT. Это единственная инструкция в скомпилированной в собственном коде хранимой процедуре, которая может передавать выполнение другой инструкции. Если инструкция SELECT отсутствует в процедуре, выполнение процедуры не передастся и она будет выполнена до начала других инструкций.  
  
 **Режим MARS и транзакции выполняющейся в памяти OLTP**  
  
 Изменения, внесенные чередующимися инструкциями и атомарными блоками, изолированы друг от друга. Например, если одна инструкция или атомарный блок вносит некоторые изменения, а затем передает выполнение другой инструкции, то новая инструкция не будет видеть изменения, внесенные первой инструкцией. Кроме того, когда первая инструкция возобновляет выполнение, она не увидит никаких изменений, внесенных другими инструкциями. Инструкции будут видеть только те изменения, которые были завершены и зафиксированы перед их запуском.  
  
 Новую пользовательскую транзакцию можно запустить в текущей пользовательской транзакции с помощью инструкции BEGIN TRANSACTION. это поддерживается только в режиме взаимодействия, поэтому BEGIN TRANSACTION может вызываться только из инструкции T-SQL, а не из хранимой процедуры, скомпилированной в собственном виде. Точку сохранения в транзакции можно создать с помощью команды сохранить ТРАНЗАКЦИю или вызова API в транзакцию. Сохраните (save_point_name), чтобы выполнить откат до точки сохранения. Эта функция также доступна только из инструкций T-SQL, а не из хранимых процедур, скомпилированных в собственном коде.  
  
 **Режим MARS и индексы columnstore**  
  
 SQL Server (начиная с версии 2016) поддерживает режим MARS с индексами columnstore. SQL Server 2014 использует функцию MARS для соединения только для чтения с таблицами с индексом columnstore.    Но SQL Server 2014 не поддерживает функцию MARS для параллельного выполнения операций DML в таблице с индексом columnstore. В этом случае SQL Server завершит подключения и прервет выполнение транзакций.   В SQL Server 2012 используются индексы columnstore только для чтения и режим MARS к ним не применяется.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает режим MARS с помощью добавления свойства инициализации источника данных SSPROP_INIT_MARSCONNECTION, реализованного в наборе свойств DBPROPSET_SQLSERVERDBINIT. Кроме того, добавлено новое ключевое слово для строки подключения — **MarsConn**. Оно принимает значения **true** и **false**. Значение по умолчанию — **false**.  
  
 Для свойства источника данных DBPROP_MULTIPLECONNECTIONS по умолчанию применяется значение VARIANT_TRUE. Это значит, что поставщик создаст несколько соединений для поддержки ряда параллельных объектов команд и наборов строк. Если включен режим MARS, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент может поддерживать несколько объектов команд и наборов строк в одном соединении, поэтому MULTIPLE_CONNECTIONS по умолчанию имеет значение VARIANT_FALSE.  
  
 Дополнительные сведения об улучшениях, появившихся в наборе свойств DBPROPSET_SQLSERVERDBINIT, см. в статье [Initialization and Authorization Properties](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md) (Свойства инициализации и авторизации).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>Пример поставщика OLE DB для собственного клиента SQL Server  
 В этом примере объект источника данных создается с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного поставщика OLE DB, а режим MARS включается с помощью свойства DBPROPSET_SQLSERVERDBINIT, установленного перед созданием объекта Session.  
  
```cpp
#include <sqlncli.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL,  
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
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента поддерживает режим MARS посредством дополнений к функциям [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) и [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) . Добавление SQL_COPT_SS_MARS_ENABLED выполнено, чтобы принять значение SQL_MARS_ENABLED_YES или SQL_MARS_ENABLED_NO; по умолчанию принимается значение SQL_MARS_ENABLED_NO. Кроме того, добавлено новое ключевое слово строки подключения, **Mars_Connection**. Оно принимает значения «да» или «нет»; по умолчанию принимается значение «нет».  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>Пример драйвера ODBC для собственного клиента SQL Server  
 В этом примере функция **SQLSetConnectAttr** используется для включения режима MARS перед вызовом функции **SQLDriverConnect** для подключения базы данных. После установки соединения вызываются две функции **SQLExecDirect** для создания двух отдельных результирующих наборов в одном соединении.  
  
```cpp
#include <sqlncli.h>  
  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_MARS_ENABLED, SQL_MARS_ENABLED_YES, SQL_IS_UINTEGER);  
SQLDriverConnect(hdbc, hwnd,   
   "DRIVER=SQL Server Native Client 10.0;  
   SERVER=(local);trusted_connection=yes;", SQL_NTS, szOutConn,   
   MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
// The 2nd execute would have failed with connection busy error if  
// MARS were not enabled.  
SQLExecDirect(hstmt1, L"SELECT * FROM Authors", SQL_NTS);  
SQLExecDirect(hstmt2, L"SELECT * FROM Titles", SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client функции](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Использование результирующих наборов по умолчанию в SQL Server](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
