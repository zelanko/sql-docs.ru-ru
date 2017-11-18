---
title: "Метод setDateTimeOffset (SQLServerCallableStatement) | Документы Microsoft"
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
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bb801d286db8f1f9a861508b15d0b50294c10419
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>Метод setDateTimeOffset (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 Задает значение указанного столбца [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Имя столбца.  
  
 *t*  
  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Вы можете получить [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение с [SQLServerCallableStatement.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md).  
  
 [setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) принимает порядковый номер столбца.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

