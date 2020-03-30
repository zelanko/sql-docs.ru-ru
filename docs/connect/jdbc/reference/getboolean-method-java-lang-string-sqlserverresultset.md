---
title: Метод getBoolean (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBoolean (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ba98a27b-722d-4904-ac65-0f082fde1fe6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a9bdf91105e9e7db82f51b5ba9885506e2edd8cd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67953530"
---
# <a name="getboolean-method-javalangstring-sqlserverresultset"></a>Метод getBoolean (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **boolean** на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getBoolean(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **boolean**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getBoolean определен с помощью метода getBoolean в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживается только для числовых и символьных типов данных. Он преобразует значения "1", 1 и "**true**" в **true**, а значения "0", 0 и "**false**" — в **false**. Для всех остальных значений поведение не определено.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBoolean (SQLServerResultSet)](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
