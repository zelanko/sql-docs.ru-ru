---
title: "Метод updateBlob (int, java.sql.Blob) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.updateBlob (int, java.sql.Blob)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e86f588-1365-4011-9412-f0acf7009880
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 603790488c2fc1f8bbef0b6e0aa1ad41e3685457
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updateblob-method-int-javasqlblob"></a>Метод updateBlob (int, java.sql.Blob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение java.sql.Blob в указанном столбце.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBlob(int index,  
                       java.sql.Blob x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
  
 **Int** , указывающее индекс столбца.  
  
 *x*  
  
 Большой двоичный объект.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateBlob указывается с помощью метода updateBlob в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBlob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

