---
title: "Метод getClientInfoProperties (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 022f09c50d0a47851e375fcbb617ee40266dbb38
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>Метод getClientInfoProperties (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает список свойств данных клиентов, поддерживаемых драйвером.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getClientInfoProperties указывается с помощью метода getClientInfoProperties в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  Этот метод возвращает пустой результирующий набор. Драйвер поддерживает только параметр **applicationName** и задает **applicationName** только во время соединения. SQL Server не поддерживает обновление данных клиентских приложений после выполнения соединения.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
