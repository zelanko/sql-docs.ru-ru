---
title: "Метод setReadOnly (SQLServerConnection) | Документы Microsoft"
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
- SQLServerConnection.setReadOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bd11fd50-f092-43a0-a6bc-c63e70cff8da
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd0efac44982bba252157a1c3dd0fd278ab4cc3e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setreadonly-method-sqlserverconnection"></a>Метод setReadOnly (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Помещает это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект в режиме только для чтения, как подсказку для драйвера JDBC включить оптимизацию базы данных.  
  
> [!NOTE]  
>  Этот метод не поддерживается [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setReadOnly(boolean readOnly)  
```  
  
#### <a name="parameters"></a>Параметры  
 *только для чтения*  
  
 **значение true,** Если соединения должен быть только для чтения. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setReadOnly указывается с помощью метода setReadOnly в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
