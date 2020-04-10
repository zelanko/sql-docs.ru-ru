---
title: Метод updateArray (int, java.sql.Array) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateArray (int, java.sql.Array)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 464f7e3f-3e8a-4b2d-aebd-1c040583d52c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c4ff7bb163935eb9c10b14b1c3e3c3b2c988171
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926067"
---
# <a name="updatearray-method-int-javasqlarray"></a>Метод updateArray (int, java.sql.Array)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец объектом Array, используя заданный индекс столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateArray(int columnIndex,  
                        java.sql.Array x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект Array.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateArray определен с помощью метода updateArray в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateArray (SQLServerResultSet)](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
