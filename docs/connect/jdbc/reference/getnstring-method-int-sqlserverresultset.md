---
title: Метод getNString (int) (SQLServerResultSet) | Документы Microsoft
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
ms.assetid: c8cc4636-01e9-4dc8-a40c-728337ca08f5
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a90e7c76d7bd1c975e9c0a3f1885bdc9c6f29f94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getnstring-method-int-sqlserverresultset"></a>Метод getNString (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как объекта String.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getNString(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект String.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getNString указывается с помощью метода getNString в интерфейсе java.sql.SQLServerResultSet.  
  
 Этот метод можно использовать для извлечения значения **nvarchar**, **nchar**, **nvarchar(max)**, **ntext**, или **xml** столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта. При попытке использования этого метода для получения значений других типов данных возникнет исключение.  
  
## <a name="see-also"></a>См. также  
 [Метод getNString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
