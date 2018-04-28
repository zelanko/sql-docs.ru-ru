---
title: Работа с изоляцией моментальных снимков | Документы Microsoft
description: Работа с изоляцией моментальных снимков в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
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
- data access [OLE DB Driver for SQL Server], snapshot isolation
- MSOLEDBSQL, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, snapshot isolation
- SQLGetInfo function
- concurrency [OLE DB Driver for SQL Server]
- SQLSetConnectAttr function
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c6fcec9fce11c4f03d92a28a0ae55ccb7e8f4d5c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="working-with-snapshot-isolation"></a>Работа с изоляцией моментального снимка
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появился новый уровень изоляции «моментального снимка», предназначенный для повышения параллелизма приложений оперативной обработки транзакций (OLTP). В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] параллелизм был основан исключительно на блокировках, что могло вызвать проблемы с блокировками и взаимоблокировками для некоторых приложений. Изоляция моментального снимка зависит от расширений управления версиями строк и предназначена для улучшения производительности путем исключения сценариев блокировки модулей чтения или записи.  
  
 Транзакции, запускаемые в режиме изоляции моментальных снимков, читают моментальный снимок базы данных на момент запуска транзакции. Управляемые набором ключей, динамических и статических серверных курсоров, открывается в контексте транзакции моментальных снимков ведут себя как очень похоже на статические курсоры, открытые в сериализуемых транзакциях. Тем не менее когда курсоры открыты блокировок уровня изоляции моментальных снимков не применяются. Этот факт может снизить блокирование на сервере.  
  
## <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server  
 Драйвер OLE DB для SQL Server включает расширения, которые используют преимущества изоляции моментального снимка, представленные в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Среди этих улучшений изменения наборов свойств DBPROPSET_DATASOURCEINFO и DBPROPSET_SESSION.  
  
### <a name="dbpropsetdatasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Набор свойств DBPROPSET_DATASOURCEINFO изменен и указывает на поддержку уровня изоляции моментальных снимков благодаря добавлению значения DBPROPVAL_TI_SNAPSHOT, используемого в свойстве DBPROP_SUPPORTEDTXNISOLEVELS. Это новое значение указывает, что уровень изоляции моментального снимка поддерживается независимо от того, включено ли в базе данных управление версиями. В следующей таблице перечислены значения DBPROP_SUPPORTEDTXNISOLEVELS:  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Тип: VT_I4<br /><br /> Только для чтения R Чтение и запись:<br /><br /> Описание: Битовая маска, указывающая поддерживаемый уровень изоляции транзакции. Сочетание может включать нуль или несколько следующих значений:<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropsetsession"></a>Набор свойств DBPROPSET_SESSION  
 Набор свойств DBPROPSET_SESSION изменен и указывает на поддержку уровня изоляции моментальных снимков благодаря добавлению значения DBPROPVAL_TI_SNAPSHOT, используемого в свойстве DBPROP_SESS_AUTOCOMMITISOLEVELS. Это новое значение указывает, что уровень изоляции моментального снимка поддерживается независимо от того, включено ли в базе данных управление версиями. В следующей таблице перечислены значения DBPROP_SESS_AUTOCOMMITISOLEVELS:
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Тип: VT_I4<br /><br /> Только для чтения R Чтение и запись:<br /><br /> Описание: Задает битовую маску, которая указывает уровень изоляции транзакций в режиме автоматической фиксации. Значения, которые могут быть установлены в этой битовой маске совпадают значения, которые могут быть установлены для DBPROP_SUPPORTEDTXNISOLEVELS.|  
  
> [!NOTE]  
>  Ошибки DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED происходят, если значение DBPROPVAL_TI_SNAPSHOT установлено при использовании версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], предшествующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Сведения о поддержке изоляции моментального снимка в транзакциях см. в разделе [поддержка локальных транзакций](../../oledb/ole-db-transactions/supporting-local-transactions.md).  

  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для компонентов SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [Свойства набора строк и поведение](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
