---
title: "Метод releaseSavepoint (SQLServerConnection) | Документы Microsoft"
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
- SQLServerConnection.releaseSavepoint
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6b625ea-c7ce-4a32-a9e0-6d2b4321bfd8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 43c5f2e735eedf959d1e72a894a5240ec3a742dc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="releasesavepoint-method-sqlserverconnection"></a>Метод releaseSavepoint (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Удаляет данный [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) объектов из текущей транзакции.  
  
> [!NOTE]  
>  Этот метод не поддерживается в настоящее время [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void releaseSavepoint(java.sql.Savepoint savepoint)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Точка сохранения*  
  
 Объект точки сохранения для удаления.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод releaseSavepoint указывается с помощью метода releaseSavepoint в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

