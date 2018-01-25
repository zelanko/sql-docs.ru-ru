---
title: "Работа с изоляцией моментальных снимков | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 848b9654969eac2a75171f1987d463ef21582736
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="working-with-snapshot-isolation"></a>Работа с изоляцией моментального снимка
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появился новый уровень изоляции «моментального снимка», предназначенный для повышения параллелизма приложений оперативной обработки транзакций (OLTP). В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] параллелизм был основан исключительно на блокировках, что могло вызвать проблемы с блокировками и взаимоблокировками для некоторых приложений. Изоляция моментального снимка зависит от расширений управления версиями строк и предназначена для улучшения производительности путем исключения сценариев блокировки модулей чтения или записи.  
  
 Транзакции, запускаемые в режиме изоляции моментальных снимков, читают моментальный снимок базы данных на момент запуска транзакции. Один из результатов состоит в том, что поведение набора ключей, динамических и статических серверных курсоров, открываемых в контексте транзакции моментальных снимков, более походит на статические курсоры, открытые в сериализуемых транзакциях. Однако, когда курсоры открыты на уровне изоляции моментальных снимков, блокировки не применяются, что может снизить блокирование на сервере.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента включает расширения для использования преимущества изоляции моментального снимка, представленные в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Среди этих улучшений изменения наборов свойств DBPROPSET_DATASOURCEINFO и DBPROPSET_SESSION.  
  
### <a name="dbpropsetdatasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Набор свойств DBPROPSET_DATASOURCEINFO изменен и указывает на поддержку уровня изоляции моментальных снимков благодаря добавлению значения DBPROPVAL_TI_SNAPSHOT, используемого в свойстве DBPROP_SUPPORTEDTXNISOLEVELS. Это новое значение указывает, что уровень изоляции моментального снимка поддерживается независимо от того, включено ли в базе данных управление версиями. Ниже приведен список значений DBPROP_SUPPORTEDTXNISOLEVELS.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Тип: VT_I4<br /><br /> Только для чтения R Чтение и запись:<br /><br /> Описание: Битовая маска, указывающая поддерживаемый уровень изоляции транзакции. Сочетание может включать нуль или несколько следующих значений:<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropsetsession"></a>Набор свойств DBPROPSET_SESSION  
 Набор свойств DBPROPSET_SESSION изменен и указывает на поддержку уровня изоляции моментальных снимков благодаря добавлению значения DBPROPVAL_TI_SNAPSHOT, используемого в свойстве DBPROP_SESS_AUTOCOMMITISOLEVELS. Это новое значение указывает, что уровень изоляции моментального снимка поддерживается независимо от того, включено ли в базе данных управление версиями. Ниже приведен список значений DBPROP_SESS_AUTOCOMMITISOLEVELS.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Тип: VT_I4<br /><br /> Только для чтения R Чтение и запись:<br /><br /> Описание: Задает битовую маску, которая указывает уровень изоляции транзакций в режиме автоматической фиксации. Значения, которые можно установить в этой битовой маске, такие же, как устанавливаемые для DBPROP_SUPPORTEDTXNISOLEVELS.|  
  
> [!NOTE]  
>  Ошибки DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED происходят, если значение DBPROPVAL_TI_SNAPSHOT установлено при использовании версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], предшествующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Сведения о поддержке изоляции моментального снимка в транзакциях см. в разделе [поддержка локальных транзакций](../../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает изоляцию моментальных снимков хотя улучшения, внесенные в [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) и [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) функции.  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 **SQLSetConnectAttr** функции теперь поддерживает использование атрибута SQL_COPT_SS_TXN_ISOLATION. Задание SQL_COPT_SS_TXN_ISOLATION значения SQL_TXN_SS_SNAPSHOT указывает, что транзакция произойдет на уровне изоляции моментального снимка.  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) функции теперь поддерживает значение SQL_TXN_SS_SNAPSHOT, будет добавлен сведения о типе SQL_TXN_ISOLATION_OPTION.  
  
 Сведения о поддержке изоляции моментального снимка в транзакциях см. в разделе [уровень изоляции транзакций курсора](../../../relational-databases/native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Свойства набора строк и поведение](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
