---
title: "Метод getBoolean (int) (SQLServerResultSet) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.getBoolean (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 50fcc0c3-36a1-47b2-b18c-7aa2ac9b27d3
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ca9e68e4feaea59103a494f696a87658d4077f1a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getboolean-method-int-sqlserverresultset"></a>Метод getBoolean (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **логическое** языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getBoolean(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **логическое** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getBoolean указывается с помощью метода getBoolean в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживается только для числовых и символьных типов данных. Он преобразует значения «1», 1, и "**true**» для **true**и значения «0», 0, и «**false**» для **false**. Для всех остальных значений поведение не определено.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBoolean &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

