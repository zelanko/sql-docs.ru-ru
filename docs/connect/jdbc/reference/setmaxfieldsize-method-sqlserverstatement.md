---
title: Метод setMaxFieldSize (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38f7fc1d-acad-4d10-9fc8-3c0669d93b07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 74d306815016e58d57418f5b72b4d4901553e8d6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925709"
---
# <a name="setmaxfieldsize-method-sqlserverstatement"></a>Метод setMaxFieldSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает ограничение количества байтов для максимального размера столбца [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), в котором хранятся символьные или двоичные значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setMaxFieldSize(int max)  
```  
  
#### <a name="parameters"></a>Параметры  
 *max*  
  
 Значение **int**, указывающее максимальное число байтов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setMaxFieldSize задается с помощью метода setMaxFieldSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
