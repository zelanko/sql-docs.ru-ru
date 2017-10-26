---
title: "Метод (int, int) supportsConvert | Документы Microsoft"
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
- SQLServerDatabaseMetaData.supportsConvert (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 54741cfd-32ac-46c5-8b09-fd60fd8833d7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4df644d58a7de3378477d09316629118a949793a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="supportsconvert-method-int-int"></a>Метод supportsConvert (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение, определяющее, поддерживает ли эта база данных операцию CONVERT для двух заданных типов SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsConvert(int fromType,  
                               int toType)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Исходный_тип*  
  
 Тип JDBC, из которого выполняется преобразование.  
  
 *toType*  
  
 Тип JDBC, в который выполняется преобразование.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод supportsConvert указывается с помощью метода supportsConvert в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Метод supportsConvert &#40; SQLServerDatabaseMetaData &#41;](../../../connect/jdbc/reference/supportsconvert-method-sqlserverdatabasemetadata.md)   
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

