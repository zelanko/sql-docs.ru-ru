---
title: "Метод (java.lang.String, java.lang.String) setClientInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b464cc1e1f63612557d6358f40b6c45cafc726e5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>Метод setClientInfo (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение указанного свойства сведений о клиенте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *name*  
  
 Строка, содержащая имя задаваемого свойства сведения клиента.  
  
 *value*  
  
 Строка, содержащая значение, задаваемое для свойства сведений о клиенте.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setClientInfo указывается с помощью метода setClientInfo в интерфейсе java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Не поддерживает свойства сведений о клиенте. В драйвере JDBC 2.0 этот метод формирует предупреждение для свойства. Приложения должны использовать [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) метод [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класс для извлечения предупреждения.  
  
## <a name="see-also"></a>См. также:  
 [Метод setClientInfo &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

