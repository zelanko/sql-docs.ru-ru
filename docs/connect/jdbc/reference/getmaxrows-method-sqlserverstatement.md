---
description: Метод getMaxRows (SQLServerStatement)
title: Метод getMaxRows (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c4fe0ef1e178b3462c51f7ab2eb9b2c85eef4dc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435536"
---
# <a name="getmaxrows-method-sqlserverstatement"></a>Метод getMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает максимальное количество строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее максимальное число строк. Если ограничения нет, то значение равно 0.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMaxRows задается с помощью метода getMaxRows в интерфейсе java.sql.Statement.  
  
 Метод getMaxRows всегда возвращает значение 0 для динамических прокручиваемых курсоров.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
