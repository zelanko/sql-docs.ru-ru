---
title: Закрытие объектов в случае использования | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b571b62a52cd25b46cc485cb7a6552bdb51b51a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="closing-objects-when-not-in-use"></a>Закрытие неиспользуемых объектов
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При работе с объектами [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], в частности [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) или одной инструкции объекты, такие как [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement ](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), их необходимо явным образом закрывать путем вызова метода close, когда они больше не нужны. При этом улучшается производительность, поскольку ресурсы драйвера и сервера освобождаются незамедлительно, а не тогда, когда сработает сборщик мусора приложения Java Virtual Machine.  
  
 Закрытие объектов особенно важно для поддержания хорошего уровня параллелизма на сервере, когда используются блокировки прокрутки. Блокировки прокрутки в буфере выборки, к которому последним осуществлялся доступ, удерживаются до тех пор, пока результирующий набор не будет закрыт. Аналогичным образом дескрипторы подготовленной инструкции удерживаются до тех пор, пока эта инструкция не будет закрыта. Если соединение используется повторно для нескольких инструкций, то закрытие инструкции перед ее выходом из области видимости позволит серверу раньше произвести очистку подготовленных дескрипторов.  
  
## <a name="see-also"></a>См. также  
 [Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
