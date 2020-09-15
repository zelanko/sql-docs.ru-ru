---
description: Метод updateFloat (int, float)
title: Метод updateFloat (int, float) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateFloat (int, float)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c9ddcd7d-1dd4-491a-99ff-6cce7f67a73b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 08757f382cd247d4b9da233e10d8eec5d906d97d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431376"
---
# <a name="updatefloat-method-int-float"></a>Метод updateFloat (int, float)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением типа **float** по заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateFloat(int index,  
                        float x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Значение **float**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateFloat определен с помощью метода updateFloat в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateFloat (SQLServerResultSet)](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
