---
title: Метод deleteRow (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc02d31a1d13a3d32f581da6fb3367473cb88bbb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955136"
---
# <a name="deleterow-method-sqlserverresultset"></a>Метод deleteRow (SQLServerResultSet)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Удаляет текущую строку из этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) и из используемой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод deleteRow задается методом deleteRow в интерфейсе Java. SQL. Result.  
  
 Этот метод не может быть вызван при нахождении курсора в строке вставки.  
  
 Если используются курсоры, управляемые набором ключей, этот метод оставляет пробел в результирующем наборе. Его наличие можно проверить с помощью метода [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md). Номера строк в результирующем наборе не изменяются.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
