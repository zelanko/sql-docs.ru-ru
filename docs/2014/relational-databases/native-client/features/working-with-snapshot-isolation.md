---
title: Работа с изоляцией моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcf2003873de6f6ca15fed4d0818337ce4920906
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63205854"
---
# <a name="working-with-snapshot-isolation"></a>Работа с изоляцией моментального снимка
  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появился новый уровень изоляции «моментального снимка», предназначенный для повышения параллелизма приложений оперативной обработки транзакций (OLTP). В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] параллелизм был основан исключительно на блокировках, что могло вызвать проблемы с блокировками и взаимоблокировками для некоторых приложений. Изоляция моментального снимка зависит от расширений управления версиями строк и предназначена для улучшения производительности путем исключения сценариев блокировки модулей чтения или записи.  
  
 Транзакции, запускаемые в режиме изоляции моментальных снимков, читают моментальный снимок базы данных на момент запуска транзакции. Один из результатов состоит в том, что поведение набора ключей, динамических и статических серверных курсоров, открываемых в контексте транзакции моментальных снимков, более походит на статические курсоры, открытые в сериализуемых транзакциях. Однако, когда курсоры открыты на уровне изоляции моментальных снимков, блокировки не применяются, что может снизить блокирование на сервере.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента OLE DB имеет улучшения, использующие преимущества изоляции моментального снимка, представленной [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]в. Среди этих улучшений изменения наборов свойств DBPROPSET_DATASOURCEINFO и DBPROPSET_SESSION.  
  
### <a name="dbpropset_datasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Набор свойств DBPROPSET_DATASOURCEINFO изменен и указывает на поддержку уровня изоляции моментальных снимков благодаря добавлению значения DBPROPVAL_TI_SNAPSHOT, используемого в свойстве DBPROP_SUPPORTEDTXNISOLEVELS. Это новое значение указывает, что уровень изоляции моментального снимка поддерживается независимо от того, включено ли в базе данных управление версиями. Ниже приведен список значений DBPROP_SUPPORTEDTXNISOLEVELS.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Тип: VT_I4<br /><br /> R/W: только для чтения<br /><br /> Описание: битовая маска, указывающая поддерживаемые уровни изоляции транзакции. Сочетание может включать нуль или несколько следующих значений:<br /><br /> — DBPROPVAL_TI_CHAOS<br />— DBPROPVAL_TI_READUNCOMMITTED<br />— DBPROPVAL_TI_BROWSE<br />— DBPROPVAL_TI_CURSORSTABILITY<br />— DBPROPVAL_TI_READCOMMITTED<br />— DBPROPVAL_TI_REPEATABLEREAD<br />— DBPROPVAL_TI_SERIALIZABLE<br />— DBPROPVAL_TI_ISOLATED<br />— DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropset_session"></a>Набор свойств DBPROPSET_SESSION  
 Набор свойств DBPROPSET_SESSION изменен и указывает на поддержку уровня изоляции моментальных снимков благодаря добавлению значения DBPROPVAL_TI_SNAPSHOT, используемого в свойстве DBPROP_SESS_AUTOCOMMITISOLEVELS. Это новое значение указывает, что уровень изоляции моментального снимка поддерживается независимо от того, включено ли в базе данных управление версиями. Ниже приведен список значений DBPROP_SESS_AUTOCOMMITISOLEVELS.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Тип: VT_I4<br /><br /> R/W: только для чтения<br /><br /> Описание: задает битовую маску, которая указывает уровень изоляции транзакции в режиме автоматической фиксации. Значения, которые можно установить в этой битовой маске, такие же, как устанавливаемые для DBPROP_SUPPORTEDTXNISOLEVELS.|  
  
> [!NOTE]  
>  Ошибки DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED происходят, если значение DBPROPVAL_TI_SNAPSHOT установлено при использовании версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], предшествующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Сведения о поддержке изоляции моментального снимка в транзакциях см. в статье [Поддержка локальных транзакций](../../native-client-ole-db-transactions/transactions.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента обеспечивает изоляцию моментального снимка, в то же самое усовершенствованные функции [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) и [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) .  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Функция **SQLSetConnectAttr** теперь поддерживает использование атрибута SQL_COPT_SS_TXN_ISOLATION. Задание SQL_COPT_SS_TXN_ISOLATION значения SQL_TXN_SS_SNAPSHOT указывает, что транзакция произойдет на уровне изоляции моментального снимка.  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 Функция [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) теперь поддерживает SQL_TXN_SS_SNAPSHOT значение, добавленное в тип сведений SQL_TXN_ISOLATION_OPTION.  
  
 Сведения о поддержке изоляции моментальных снимков в транзакциях см. в разделе [уровень изоляции транзакций курсора](../../native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client функции](sql-server-native-client-features.md)   
 [Свойства и поведение наборов строк](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
