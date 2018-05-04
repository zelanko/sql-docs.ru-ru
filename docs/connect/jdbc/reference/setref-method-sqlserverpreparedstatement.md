---
title: Метод (SQLServerPreparedStatement) setRef | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setRef
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a09bbf9-6f8f-4a21-85d2-2182111b5ce7
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e68bb9e5b6651728f5dd3380d8ec76ca8f4dc103
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setref-method-sqlserverpreparedstatement"></a>Метод (SQLServerPreparedStatement) setRef
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру для заданного объекта ссылки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setRef(int i,  
                         java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Я*  
  
 **Int** указывает номер параметра.  
  
 *x*  
  
 Объект ссылки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setRef указывается с помощью метода setRef в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
