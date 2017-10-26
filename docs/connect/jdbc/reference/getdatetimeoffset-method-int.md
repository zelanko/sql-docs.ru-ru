---
title: "Метод getDateTimeOffset (int) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb00356-4d6e-4625-b924-67646930fdf2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3171789255d0184715917429c7627aadd734d62e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getdatetimeoffset-method-int"></a>Метод getDateTimeOffset (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 Получает значение указанного параметра в виде [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта на Java по заданному индексу параметра языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int index)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
  
 Начинающийся с единицы порядковый номер параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Можно задать [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение параметра с [SQLServerCallableStatement.setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод getDateTimeOffset &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

