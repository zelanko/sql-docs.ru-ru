---
title: "Метод (SQLServerConnection) getCatalog | Документы Microsoft"
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
apiname:
- SQLServerConnection.getCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac9650ac08ac3cae7169a2f746d050ccbed7d6f6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getcatalog-method-sqlserverconnection"></a>getCatalog метод (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущее имя каталога этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее имя каталога.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getCatalog указывается с помощью getCatalog метода в интерфейсе java.sql.Connection.  
  
 Возвращает текущее свойство каталога для объекта SQLServerConnection, или значение null, если оно не задано. Свойство каталога задано явно с [setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md) метода или обновляется неявно при считывании изменения среды табличных данных для текущего каталога.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

