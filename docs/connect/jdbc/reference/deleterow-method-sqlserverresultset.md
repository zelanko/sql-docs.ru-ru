---
title: Метод deleteRow (SQLServerResultSet) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 987be5ee9fd49385acf02e52108e1e657fbc08a4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786523"
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
 Этот метод deleteRow указывается с помощью метода deleteRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не может быть вызван при нахождении курсора в строке вставки.  
  
 Если используются курсоры, управляемые набором ключей, этот метод оставляет пробел в результирующем наборе. Можно проверить наличие такого пробела методом [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md). Номера строк в результирующем наборе не изменяются.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
