---
title: Использование множественных активных результирующих наборов (MARS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 32f96c6eec4f56d50d210ecac63014c166f37ac4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428983"
---
# <a name="using-multiple-active-result-sets-mars"></a>Использование режима MARS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

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
>  По умолчанию функции режима MARS не активированы. Чтобы использовать режим MARS при подключении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] к собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], необходимо явно задействовать его внутри строки соединения. Дополнительные сведения см. в подразделах «Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]» и «Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]» далее в этом разделе.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не ограничивает число активных инструкций в соединении.  
  
 Типичные приложения, которые обходятся одновременным выполнением не более чем одного пакета из нескольких инструкций или одной хранимой процедуры, лучше запускать в режиме MARS; при этом они не обязательно должны понимать, как именно реализован режим MARS. Однако приложения с более сложными требованиями должны принимать это во внимание.  
  
 Режим MARS дает возможность поочередно выполнять несколько запросов с использованием одного соединения. Иначе говоря, существует возможность выполнения пакета с одновременным выполнением других запросов. Впрочем, надо отметить, что режим MARS определяется в терминах чередования, а не в терминах параллельного выполнения.  
  
 Инфраструктура режима MARS предоставляет возможность поочередного выполнения нескольких пакетов, хотя выполнение может переключаться лишь в четко определенных пунктах. Кроме того, почти все инструкции должны выполняться атомарным образом внутри пакета. Инструкции, возвращающие строки клиенту, который иногда называются *точками выхода*, могут поочередно до завершения, а строки отправляются клиенту, например:  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Все иные инструкции, выполняемые как часть хранимой процедуры или пакета, должны выполняться до конца, и только после этого выполнение может быть передано другим запросам MARS.  
  
 Точный порядок чередования выполнения пакетов определяется рядом факторов, поэтому предугадать точную последовательность выполнения содержащих точки выхода команд из нескольких пакетов затруднительно. Необходимо проявлять осторожность, чтобы избегать нежелательных побочных эффектов, которые вызываются поочередным выполнением подобных сложных пакетов.  
  
 Вы сможете избежать проблем, если при управлении состоянием соединений (SET, USE) и транзакциями (BEGIN TRAN, COMMIT, ROLLBACK) будете использовать вызовы API, а не инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)], если не будете включать эти инструкции в пакеты из нескольких инструкций, также содержащие точки выхода, и если будете сериализовать выполнение таких пакетов посредством использования либо отмены всех результатов.  
  
> [!NOTE]  
>  Пакет хранимых процедур, начинающий ручную или неявную транзакцию с активированным режимом MARS, должен завершать транзакцию до выхода пакета. В противном случае по завершении выполнения пакета [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] осуществляет откат всех изменений, внесенных транзакцией. Такая транзакция управляется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как транзакция контекста пакета. Это новый тип транзакции, реализованный в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] с тем, чтобы существующие верно выполняемые хранимые процедуры можно было использовать в режиме MARS. Дополнительные сведения о транзакциях контекста пакета см. в разделе [инструкции транзакций &#40;Transact-SQL&#41;](~/t-sql/statements/statements.md).  
  
 Пример использования режима MARS в ADO, см. в разделе [использование объектов ADO с SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="in-memory-oltp"></a>In-Memory OLTP  
 OLTP в памяти поддерживает режим MARS, с помощью запросов и скомпилированной хранимой процедуры. Режим MARS дает возможность запрашивает данные из нескольких запросов без необходимости полностью получения каждого результирующего набора перед отправкой запроса для получения строк из нового результирующего набора. Чтобы успешно прочитан из нескольких открытые результирующие наборы, необходимо использовать режим MARS включить подключения.  
  
 Режим MARS отключен по умолчанию, поэтому необходимо явно включить его, добавив `MultipleActiveResultSets=True` на строку подключения. Следующий пример демонстрирует, как соединиться с экземпляром SQL Server и указать, что включен режим MARS:  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS с In-Memory OLTP — это по сути так же, как режим MARS в остальной части SQL engine. Ниже перечислены отличия при использовании режима MARS в оптимизированных для памяти таблиц и скомпилированных в собственном коде компиляции хранимых процедур.  
  
 **Режим MARS и оптимизированных для памяти таблиц**  
  
 Ниже приведены различия между таблицами на диске и оптимизированных для памяти, при использовании режима MARS с поддержкой подключения.  
  
-   Две инструкции может изменять данные в тот же целевой объект, но если они оба пытаются изменить ту же запись конфликт записи приведет к новой операции переход на другой. Тем не менее если обе операции изменения различных записей, операции будут успешно выполнены.  
  
-   Каждая инструкция выполняется в режиме изоляции моментального СНИМКА, поэтому новые операции не видим изменения, внесенные с помощью существующих инструкций. Даже если параллельных операторы выполняются в одной транзакции SQL engine создает контекста пакета транзакций для каждой инструкции, которые изолированы друг от друга. Тем не менее транзакции контекста пакета по-прежнему связаны друг с другом, отката одной транзакции контекста пакета влияет на другие формулы в том же пакете.  
  
-   DDL-операции не допускаются в пользовательских транзакциях, чтобы они сразу же не удастся.  
  
 **Режим MARS и скомпилированные в собственном коде хранимых процедур**  
  
 Скомпилированные хранимые процедуры могут выполняться в подключения с включенным режимом MARS и может уступить выполнение другой инструкции только в том случае, когда встречается точки приостановки. Точки приостановки требуется инструкция SELECT, которая является единственной инструкцией в скомпилированную в собственном коде хранимой процедуре, можно передать выполнение другой инструкции. Если инструкции SELECT не присутствует в процедуру, которую не получится, его будут выполняться до конца, прежде чем начать других инструкций.  
  
 **Операции режима MARS и In-memory OLTP**  
  
 Изменения, произведенные инструкций и атомарные блоки, которые чередуются изолированы друг от друга. Например одной инструкции или блока atomic вносит некоторые изменения, а затем выдает выполнение другой инструкции, новый оператор недоступен для изменения, внесенные в первой инструкции. Кроме того когда первая инструкция возобновляет выполнение, он не увидит любые изменения, внесенные другими инструкциями. Инструкции будут видеть только изменения, которые являются завершения и фиксации, прежде чем начинается оператор.  
  
 Можно запустить новую транзакцию пользователя в текущей транзакции пользователя, с помощью инструкции BEGIN TRANSACTION — это поддерживается только в режиме взаимодействия, поэтому инструкции BEGIN TRANSACTION может вызываться только из инструкции T-SQL и не из в скомпилированной хранимой процедура. Можно создать сохранения точки в транзакции, использующей SAVE TRANSACTION или вызов API к транзакции. Save(save_point_name) для отката до точки сохранения. Эта функция включена только из инструкций T-SQL, а не из в скомпилированной хранимой процедуры.  
  
 **Режим MARS и индексы columnstore**  
  
 SQL Server (начиная с 2016) поддерживает режим MARS с индексами columnstore. SQL Server 2014 использует функцию MARS для соединения только для чтения с таблицами с индексом columnstore.    Но SQL Server 2014 не поддерживает функцию MARS для параллельного выполнения операций DML в таблице с индексом columnstore. В этом случае SQL Server будет завершать соединения и прервать транзакции.   SQL Server 2012 содержит индексы columnstore только для чтения и режим MARS не применяется к ним.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает режим MARS путем добавления SSPROP_INIT_MARSCONNECTION данных свойства инициализации источника, которое реализовано в наборе свойств dbpropset_sqlserverdbinit. Кроме того, ключевое слово строки новое соединение **MarsConn**, как были добавлены. Он принимает **true** или **false** значения; **false** используется по умолчанию.  
  
 Для свойства источника данных DBPROP_MULTIPLECONNECTIONS по умолчанию применяется значение VARIANT_TRUE. Это значит, что поставщик создаст несколько соединений для поддержки ряда параллельных объектов команд и наборов строк. Если включен режим MARS, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client может поддерживать несколько объектов команд и наборов строк в одном соединении, поэтому MULTIPLE_CONNECTIONS по умолчанию задано значение VARIANT_FALSE.  
  
 Дополнительные сведения о усовершенствования, внесенные в наборе свойств DBPROPSET_SQLSERVERDBINIT, см. в разделе [свойства инициализации и авторизации](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>Пример поставщика OLE DB для собственного клиента SQL Server  
 В этом примере объект источника данных создается с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного и режим MARS включен с помощью свойств DBPROPSET_SQLSERVERDBINIT перед созданием объекта сеанса.  
  
```  
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
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает режим MARS посредством добавлений к [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) и [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) функции. Добавление SQL_COPT_SS_MARS_ENABLED выполнено, чтобы принять значение SQL_MARS_ENABLED_YES или SQL_MARS_ENABLED_NO; по умолчанию принимается значение SQL_MARS_ENABLED_NO. Кроме того, ключевое слово строки новое соединение **Mars_Connection**, как были добавлены. Оно принимает значения «да» или «нет»; по умолчанию принимается значение «нет».  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>Пример драйвера ODBC для собственного клиента SQL Server  
 В этом примере **SQLSetConnectAttr** функция используется для включения функции MARS перед вызовом **SQLDriverConnect** для подключения к базе данных. После подключения двух **SQLExecDirect** функции вызываются для создания двух отдельных результирующих наборов для одного соединения.  
  
```  
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
SQLExecDirect(hstmt1, L”SELECT * FROM Authors”, SQL_NTS);  
SQLExecDirect(hstmt2, L”SELECT * FROM Titles”, SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Использование результирующих наборов по умолчанию в SQL Server](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
