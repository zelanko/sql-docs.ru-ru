---
title: "Метод getClientInfo () | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed81345b9cf45678fd4571fca747eebb7fc30f9b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getclientinfo-method-"></a>Метод getClientInfo ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает список, содержащий имя и текущее значение всех свойств данных клиентов, поддерживаемых драйвером JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект свойств, содержащий имя и текущее значение всех свойств данных клиентов, поддерживаемых драйвером.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getClientInfo указывается с помощью метода getClientInfo в интерфейсе java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Не поддерживает свойства сведений о клиенте. В результате этот метод возвращает пустой объект свойства.  
  
 Аналогичным образом, приложения могут использовать [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) метод [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) класс, чтобы получить список свойств данных клиентов, поддерживаемых драйвером. [GetClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) метод возвращает пустой результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Метод getClientInfo &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

