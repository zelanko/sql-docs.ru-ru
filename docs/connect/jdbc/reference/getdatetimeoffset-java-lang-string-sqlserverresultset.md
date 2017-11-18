---
title: "метод getDateTimeOffset(java.lang.string) (SQLServerResultSet) | Документы Microsoft"
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
ms.assetid: e585927c-0dee-43fd-b71e-c9f1701790bd
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26baa74f60cf04c712d6e8c6a0addec057893109
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getdatetimeoffsetjavalangstring-sqlserverresultset"></a>Метод getDateTimeOffset(java.lang.string) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 Получает значение указанного столбца в виде [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта на Java по заданному индексу параметра языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Вы можете обновить [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение с [помощью SQLServerResultSet.updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

