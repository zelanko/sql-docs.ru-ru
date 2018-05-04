---
title: Метод updateFloat (int, float) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateFloat (int, float)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c9ddcd7d-1dd4-491a-99ff-6cce7f67a73b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc127fd05be610d957063373b4d953ff917c8b83
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updatefloat-method-int-float"></a>Метод updateFloat (int, float)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с **float** значение заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateFloat(int index,  
                        float x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 **Int** , указывающее индекс столбца.  
  
 *x*  
  
 Объект **float** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateFloat указывается с помощью метода updateFloat в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также  
 [Метод updateFloat &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
