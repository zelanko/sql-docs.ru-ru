---
title: "Метод isValid (SQLServerConnection) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed5a2cb3da3fd5ac503f002f3da3dd4dd90a3e77
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="isvalid-method-sqlserverconnection"></a>Метод isValid (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта не была закрыта и все еще действителен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *время ожидания*  
  
 **Int** , указывающее количество секунд ожидания при проверке соединения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если подключение является допустимым; **false** Если подключение не является допустимым или допустимость соединения не удается определить до истечения времени ожидания.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод isValid определяется isValid-метод в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
