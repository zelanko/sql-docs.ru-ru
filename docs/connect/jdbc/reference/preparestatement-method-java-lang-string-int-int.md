---
description: Метод prepareStatement (java.lang.String, int, int)
title: Метод prepareStatement (java.lang.String, int, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9cbb24ea7e33779665b80a8a967f739df4b74baa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432916"
---
# <a name="preparestatement-method-javalangstring-int-int"></a>Метод prepareStatement (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), который создает объекты [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) с заданным типом и видом параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sSql*  
  
 Значение **String**, содержащее инструкцию SQL.  
  
 *resultSetType*  
  
 Значение **int**, указывающее тип результирующего набора.  
  
 *resultSetConcurrency*  
  
 Значение **int**, указывающее тип параллелизма результирующего набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект PreparedStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод prepareStatement определяется методом prepareStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
