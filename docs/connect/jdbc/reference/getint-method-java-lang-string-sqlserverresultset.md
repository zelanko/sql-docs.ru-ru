---
description: Метод getInt (java.lang.String) (SQLServerResultSet)
title: Метод getInt (java.lang.String) (SQLServerResultSet) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getInt (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 76b7054d-46dd-4d87-93a4-a7ea2ae9b7fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3449a5e97b71bdc744790f21fc6410a51ff1329f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435856"
---
# <a name="getint-method-javalangstring-sqlserverresultset"></a>Метод getInt (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа **int** на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getInt(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getInt определен с помощью метода getInt в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживается только для типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], таких как int, smallint, tinyint и bit, которые могут безопасно возвращать целочисленное значение. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод getInt (SQLServerResultSet)](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
