---
title: "Метод setLoginTimeout (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e95a0377de7fe9a901f33b5913e70399b298aba
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Метод setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает количество секунд, которое это [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) будет ждать объект при попытке установить соединение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *loginTimeout*  
  
 **Int** значение, представляющее количество секунд ожидания. Нулевое значение означает, что время ожидания равно системному времени ожидания по умолчанию, т.е. 15 секундам.  
  
## <a name="remarks"></a>Замечания  
 Этот метод setLoginTimeout указывается с помощью метода setLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
