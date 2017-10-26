---
title: "Метод updateNString (int, java.lang.String) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb909f1-4a96-4be1-adea-36c8d9703112
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7889388394722a0b049f198c6ac7ac8473872297
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updatenstring-method-int-javalangstring"></a>Метод updateNString (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с **строка** с использованием индекса указанного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNString(int columnIndex,  
                        java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
 *nString*  
  
 Объект **строка** объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateNString указывается с помощью метода updateNString в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает Java **строка** к выбранному **nchar**, **nvarchar(max)**, **ntext**, и **xml** столбцы. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNString &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

