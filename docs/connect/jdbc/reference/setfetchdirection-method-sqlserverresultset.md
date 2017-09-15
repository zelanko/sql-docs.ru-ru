---
title: "Метод setFetchDirection (SQLServerResultSet) | Документы Microsoft"
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
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd6ab9a94acf883ed27cdd79fee886b6c54ca596
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setfetchdirection-method-sqlserverresultset"></a>Метод setFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Дает указание относительно направления, в котором строки в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта будет обработан.  
  
> [!NOTE]  
>  Этот метод не поддерживается в настоящее время [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При использовании этого метода драйвер JDBC запоминает настройки, но не использует их в текущий момент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Направление*  
  
 **Int** Указывает предполагаемое направление выборки. Может использоваться одно из следующих значений:  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setFetchDirection указывается с помощью метода setFetchDirection в интерфейсе java.sql.ResultSet.  
  
 Начальное значение этого метода определяется [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект, который был создан этот объект SQLServerResultSet. Направление выборки может быть изменено в любой момент.  
  
> [!NOTE]  
>  Если курсор однопроходной, то при использовании этого метода направление изменено не будет.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
