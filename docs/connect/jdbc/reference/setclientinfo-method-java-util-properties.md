---
title: "Метод setClientInfo (java.util.Properties) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3484e23a4f7e8997d1bfa21a34a4cdf6f6dee71
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setclientinfo-method-javautilproperties"></a>Метод setClientInfo (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение свойств сведений о клиенте для соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Свойства*  
  
 Объект свойств, содержащий список задаваемых свойств сведений клиента.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setClientInfo указывается с помощью метода setClientInfo в интерфейсе java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Не поддерживает свойства сведений о клиенте. Этот метод формирует предупреждения, если *свойства* входной параметр не ссылается на пустой набор свойств. Другими словами, этот метод формирует предупреждения для свойств, которые нужно задать в приложении. Приложения должны использовать [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) метод [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класс для извлечения каждого предупреждения.  
  
## <a name="see-also"></a>См. также:  
 [Метод setClientInfo &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

