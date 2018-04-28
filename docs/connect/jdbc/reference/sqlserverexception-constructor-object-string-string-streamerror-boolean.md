---
title: Конструктор SQLServerException (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2aa5485f6568d2a01655e273f57b07448c7590d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-streamerror-boolean"></a>Конструктор SQLServerException (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) класса для заданного **объекта**, **строка** объекта, **строка** объект,  **StreamError** объекта и **логическое**.

## <a name="syntax"></a>Синтаксис  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            StreamError streamError,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>Параметры  
 *OBJ*  
  
 Буфер ввода-ВЫВОДА, сформировавшего исключение.

 *errText*  
  
 Строка, содержащая текст ошибки.
  
 *sqlState*  
  
 Объект перечисления, который содержит сведения о состоянии SQL.
 
 *streamError*  
  
 Объект StreamError, содержащий сведения об ошибке.
 
 *bStack*  
  
 Логическое значение, указывающее, если следует создавать трассировки стека.
  
## <a name="see-also"></a>См. также  
 [Конструкторы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Класс SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
