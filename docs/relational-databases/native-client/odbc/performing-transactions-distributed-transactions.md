---
title: Выполнение распределенных транзакций | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4375f4561368540c5411342748982db6d79a1088
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="performing-transactions---distributed-transactions"></a>Выполнение транзакций - распределенных транзакций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  С помощью координатора распределенных транзакций (Майкрософт) (MS DTC) приложения могут распространять транзакции на два или более экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Он также позволяет приложениям участвовать в транзакциях, выполняющихся под управлением диспетчеров транзакций, которые соответствуют стандарту Open Group DTP XA.  
  
 Обычно все команды управления транзакциями отправляются на сервер через драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Приложение запускает транзакцию путем вызова [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с выключенным режимом автоматической фиксации. Затем приложение выполняет обновления, состоящие из транзакции и вызовов [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) с параметром SQL_COMMIT или SQL_ROLLBACK.  
  
 При использовании MS DTC, однако MS DTC становится диспетчера транзакций и приложение больше не использует **SQLEndTran**.  
  
 В случае прикрепления к одной распределенной транзакции, а затем ко второй драйвер ODBC Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] покидает исходную распределенную транзакцию и прикрепляется к новой транзакции. Дополнительные сведения см. в разделе [Справочник по программированию DTC](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>См. также  
 [Выполнение транзакций & #40; ODBC & #41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
