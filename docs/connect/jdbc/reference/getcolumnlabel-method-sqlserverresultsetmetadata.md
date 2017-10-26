---
title: "Метод getColumnLabel (SQLServerResultSetMetaData) | Документы Microsoft"
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
- SQLServerResultSetMetaData.getColumnLabel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cf67692c-24aa-49e6-8e88-a47d4e8c021c
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e4ae1d35dee8b76aedf67b69833a445cd2f9ff76
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumnlabel-method-sqlserverresultsetmetadata"></a>Метод getColumnLabel (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает предлагаемое название указанного столбца для использования при отображении и выводе на печать.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getColumnLabel(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *столбец*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее название столбца.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getColumnLabel указывается с помощью метода getColumnLabel в интерфейсе java.sql.ResultSetMetaData.  
  
 Этот метод возвращает псевдоним столбца. Если псевдоним недоступен, этот метод возвращает имя столбца.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

