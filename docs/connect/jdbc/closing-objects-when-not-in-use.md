---
title: Закрытие объектов, когда не используется | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2a9539599848f86a84cd03838c1fa7412c24fb1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957309"
---
# <a name="closing-objects-when-not-in-use"></a>Закрытие неиспользуемых объектов
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Во время работы с объектами [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], в частности [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) или другими объектами Statement, например [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), когда они больше не нужны, то их необходимо закрывать, используя методы close. При этом улучшается производительность, поскольку ресурсы драйвера и сервера освобождаются незамедлительно, а не тогда, когда сработает сборщик мусора приложения Java Virtual Machine.  
  
 Закрытие объектов особенно важно для поддержания хорошего уровня параллелизма на сервере, когда используются блокировки прокрутки. Блокировки прокрутки в буфере выборки, к которому последним осуществлялся доступ, удерживаются до тех пор, пока результирующий набор не будет закрыт. Аналогичным образом дескрипторы подготовленной инструкции удерживаются до тех пор, пока эта инструкция не будет закрыта. Если соединение используется повторно для нескольких инструкций, то закрытие инструкции перед ее выходом из области видимости позволит серверу раньше произвести очистку подготовленных дескрипторов.  
  
## <a name="see-also"></a>См. также:  
 [Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
