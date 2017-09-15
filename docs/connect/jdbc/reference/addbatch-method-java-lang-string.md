---
title: "Метод addBatch (java.lang.String) | Документы Microsoft"
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
- SQLServerPreparedStatement.addBatch (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 093f6c3b-49a6-4043-9993-bd0482de04dd
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8febab83df94f0d1f6034c133cdd7e5a95db51ad
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="addbatch-method-javalangstring"></a>Метод addBatch (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Добавляет заданную команду SQL в текущий список команд для данного [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *SQL*  
  
 Объект **строка** , содержащий инструкции SQL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод addBatch указывается с помощью метода addBatch в интерфейсе java.sql.Statement.  
  
 Вызов этого метода будет приведет к исключению, поскольку задан в инструкции SQL для объекта SQLServerPreparedStatement при создании объекта.  
  
## <a name="see-also"></a>См. также:  
 [Метод addBatch &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
