---
description: Метод setBigDecimal (SQLServerPreparedStatement)
title: Метод setBigDecimal (SQLServerPreparedStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setBigDecimal
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 860f86db-d840-401a-a5c2-cd22e8cc1e4e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a1422fe5b6b2e84cfdbdcde353c0acb9619c847
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432526"
---
# <a name="setbigdecimal-method-sqlserverpreparedstatement"></a>Метод setBigDecimal (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер назначенного параметра для указанного объекта BigDecimal.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setBigDecimal(int n,  
                                java.math.BigDecimal x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 Значение **int**, определяющее номер параметра.  
  
 *x*  
  
 Объект BigDecimal.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setBigDecimal задается с помощью метода setBigDecimal в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
