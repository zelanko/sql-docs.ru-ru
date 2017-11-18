---
title: "Метод setCursorName (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.setCursorName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3f3ec4f2-103a-4e16-9206-c5bd8639f946
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 501440dec2f47c4f3f272ebde7f6cbd01642e377
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setcursorname-method-sqlserverstatement"></a>Метод setCursorName (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает имени курсора SQL значение заданной строки. Это значение будет использоваться при дальнейших вызовах метода execute.  
  
> [!NOTE]  
>  Этот метод не поддерживается в настоящее время [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При вызове этого метода изменения не происходят.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCursorName(java.lang.String name)  
```  
  
#### <a name="parameters"></a>Параметры  
 *name*  
  
 Объект **строка** , содержащее имя курсора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setCursorName указывается с помощью метода setCursorName в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

