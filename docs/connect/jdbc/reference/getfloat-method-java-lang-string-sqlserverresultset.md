---
description: Метод getFloat (java.lang.String) (SQLServerResultSet)
title: Метод getFloat (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFloat (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 09491a8a-1931-411e-9b35-2b269c1b7f12
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c808dc2308d6f4c4a8582045b474bc05aa4d27d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435986"
---
# <a name="getfloat-method-javalangstring-sqlserverresultset"></a>Метод getFloat (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения **float** на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public float getFloat(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **float**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFloat определен с помощью метода getFloat в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает все числовые типы с точностью Java **float**.  
  
## <a name="see-also"></a>См. также:  
 [Метод getFloat (SQLServerResultSet)](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
