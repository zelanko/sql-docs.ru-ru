---
description: Метод position (java.sql.Clob, long)
title: Метод position (java.sql.Clob, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.position (java.sql.Clob, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2fb34d5-1d34-4764-a795-712d9c6aa313
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d782839bc1a68008c4e86231fdf436b8c6f7a580
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433026"
---
# <a name="position-method-javasqlclob-long"></a>Метод position (java.sql.Clob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает позицию символа указанного объекта CLOB в CLOB по заданной начальной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public long position(java.sql.Clob searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *searchstr*  
  
 Подстрока для поиска.  
  
 *start*  
  
 Позиция, с которой начинается поиск. Позиция отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Позиция, в которой находится подстрока, либо значение -1, если она не найдена. Позиция отсчитывается от 1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод position задается с помощью метода position в интерфейсе java.sql.Clob.  
  
## <a name="see-also"></a>См. также:  
 [Метод position (SQLServerClob)](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
