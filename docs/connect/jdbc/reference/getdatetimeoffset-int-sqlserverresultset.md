---
title: "метод getDateTimeOffset(int) (SQLServerResultSet) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60abf83d-6f97-4e47-b9d3-5072bd09d869
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f74f890ae244b3a6d1672f53f2d6788c9e813744
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getdatetimeoffsetint-sqlserverresultset"></a>Метод getDateTimeOffset(int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 Получает значение указанного столбца в виде [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта на Java по заданному индексу параметра языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Порядковый номер столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Вы можете обновить [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение с [помощью SQLServerResultSet.updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

