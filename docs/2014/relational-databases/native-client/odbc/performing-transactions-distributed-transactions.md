---
title: Выполнение распределенных транзакций | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d6c03f674722e817fc8c16dd712572c3236e73d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099545"
---
# <a name="performing-distributed-transactions"></a>Выполнение распределенных транзакций
  С помощью координатора распределенных транзакций (Майкрософт) (MS DTC) приложения могут распространять транзакции на два или более экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Он также позволяет приложениям участвовать в транзакциях, выполняющихся под управлением диспетчеров транзакций, которые соответствуют стандарту Open Group DTP XA.  
  
 Обычно все команды управления транзакциями отправляются на сервер через драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Приложение запускает транзакцию путем вызова [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) с выключенным режимом автоматической фиксации. Затем приложение выполняет обновления, состоящие из транзакции и вызовов [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) с параметром SQL_COMMIT или SQL_ROLLBACK.  
  
 При использовании MS DTC, однако MS DTC становится диспетчера транзакций и приложение больше не использует **SQLEndTran**.  
  
 В случае прикрепления к одной распределенной транзакции, а затем ко второй драйвер ODBC Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] покидает исходную распределенную транзакцию и прикрепляется к новой транзакции. Дополнительные сведения см. в разделе [Справочник по программированию DTC](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>См. также  
 [Выполнение транзакций &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  