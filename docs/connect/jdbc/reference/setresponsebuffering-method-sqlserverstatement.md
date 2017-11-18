---
title: "Метод setResponseBuffering (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c5af0e179ea15fc4d5a30604b606f5ff45c79a1b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>Метод setResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта без учета регистра **полная строка** или **адаптивной**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *value*  
  
 Объект **строка** , содержащий режим буферизации ответов. Допустимый режим может принимать одно из следующих строк без учета регистра: **полного** или **адаптивной**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 **Адаптивная** указывает на буферизацию минимума данных при необходимости.  
  
 **Полный** указывает считывание всех результатов с сервера во время выполнения.  
  
 Адаптивная значение по умолчанию в версии 2.0 и 3.0 драйвера JDBC. Full использовалось по умолчанию до версии 2.0 драйвера JDBC.  
  
 [SetResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод позволяет переопределять **responseBuffering** подключения **строка** свойств для текущего [ SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта. Дополнительные сведения об использовании режима буферизации ответов см. в разделе [с помощью адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Если приложение указывает недопустимое значение параметра для [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метода [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) возникает исключение.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Использование адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  

