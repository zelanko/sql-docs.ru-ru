---
description: Метод getTime (int) (SQLServerResultSet)
title: Метод getTime (int) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTime (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e18c84f5-7171-4057-8c9e-fe1d43ae9c20
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e14e3926f318b0fca2fe6b9f7dc966799befd0aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434256"
---
# <a name="gettime-method-int-sqlserverresultset"></a>Метод getTime (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного индекса столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Time на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Time.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTime определен с помощью метода getTime в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает допустимую часть типа данных datetime или smalldatetime [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с частью даты, заданной в виде базовой даты Java, — 1 января 1970 г.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTime (SQLServerResultSet)](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
