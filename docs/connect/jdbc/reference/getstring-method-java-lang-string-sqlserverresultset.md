---
title: Метод getString (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a98c8a8-61d0-40c9-9335-25a87b732dc3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da5cf4ad735ee650ea87f70687b5f22575921144
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926214"
---
# <a name="getstring-method-javalangstring-sqlserverresultset"></a>Метод getString (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения **String** на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getString(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getString определен с помощью метода getString в интерфейсе java.sql.ResultSet.  
  
 Все столбцы в SQL Server можно возвращать как тип String. Это значит, что можно возвращать представление **String** всех числовых и символьных типов, а также шестнадцатеричное представление двоичных столбцов, таких как binary, varbinary, varbinary(max), image, timestamp и uniqueidentifier.  
  
 Типы, зависящие от расположения, такие как money, smallmoney, datetime, smalldatetime, float, real, decimal и numeric, возвращают канонический формат toString() для базового значения типа.  
  
 Определяемые пользователем типы возвращаются в виде шестнадцатеричных значений **String**.  
  
## <a name="see-also"></a>См. также:  
 [Метод getString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
