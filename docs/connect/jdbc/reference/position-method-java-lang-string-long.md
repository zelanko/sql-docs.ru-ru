---
title: Метод position (java.lang.String, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.position (java.lang.String, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 86fad8ed-375a-42e1-b40e-1fa085957a2c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ed0a62940fc29e2d909678dabec784a906c02515
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67976440"
---
# <a name="position-method-javalangstring-long"></a>Метод position (java.lang.String, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает позицию символа указанной подстроки в CLOB по заданной начальной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public long position(java.lang.String searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *searchstr*  
  
 Подстрока для поиска.  
  
 *start*  
  
 Позиция, с которой начнется поиск; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Позиция, в которой находится подстрока, либо значение -1, если она не найдена. Первая позиция имеет номер 1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод position задается с помощью метода position в интерфейсе java.sql.Clob.  
  
## <a name="see-also"></a>См. также:  
 [Метод position (SQLServerClob)](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
