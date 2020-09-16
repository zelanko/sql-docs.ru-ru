---
description: Метод getFetchSize (SQLServerResultSet)
title: Метод getFetchSize (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7bc96930-b0c9-42f6-8df9-1d8d824408b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e04f4b2b852884f84888edbf19103c17b1508bed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436036"
---
# <a name="getfetchsize-method-sqlserverresultset"></a>Метод getFetchSize (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение размера выборки для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getFetchSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое указывает текущий размер выборки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFetchSize задается с помощью метода getFetchSize в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
