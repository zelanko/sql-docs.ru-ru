---
title: Метод updateInt (int, int) | Документы Microsoft
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
- SQLServerResultSet.updateInt (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f4f651b0-a822-4bd4-b391-cc2355154a2a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9834e460d6b5ed7296480e51496617126094efdb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updateint-method-int-int"></a>Метод updateInt (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с **int** значение заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateInt(int index,  
                      int x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 **Int** , указывающее индекс столбца.  
  
 *x*  
  
 **Int** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateInt указывается с помощью метода updateInt в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также  
 [Метод updateInt &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
