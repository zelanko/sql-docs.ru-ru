---
title: Метод getBoolean (int) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBoolean (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 50fcc0c3-36a1-47b2-b18c-7aa2ac9b27d3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3380b26cb0401e35c59b50b349c279566612c50f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66771644"
---
# <a name="getboolean-method-int-sqlserverresultset"></a>Метод getBoolean (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **boolean** на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getBoolean(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **boolean**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getBoolean определен с помощью метода getBoolean в интерфейсе java.sql.CallableStatement.  
  
 Этот метод поддерживается только для числовых и символьных типов данных. Он преобразует значения «1», 1, и "**true**" для **true**и значения «0», 0, и "**false**" для **false**. Для всех остальных значений поведение не определено.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBoolean (SQLServerResultSet)](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
