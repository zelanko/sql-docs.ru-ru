---
description: Метод getResultSetConcurrency (SQLServerStatement)
title: Метод getResultSetConcurrency (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 47ef6547-5ec7-4cf5-a4d4-e34cbeec72eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c8cdec4c233f2a7d9241d63e3c1e6e29265157fa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434776"
---
# <a name="getresultsetconcurrency-method-sqlserverstatement"></a>Метод getResultSetConcurrency (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает параллелизм результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getResultSetConcurrency()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее тип параллелизма результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getResultSetConcurrency задается с помощью метода getResultSetConcurrency в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
