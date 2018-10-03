---
title: Метод supportsSubqueriesInExists (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSubqueriesInExists
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 14c08c7f-5c1e-4e21-8373-ae32c22e47d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a924d4aa813f86d24579d918072b13ec3521ee57
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737062"
---
# <a name="supportssubqueriesinexists-method-sqlserverdatabasemetadata"></a>Метод supportsSubqueriesInExists (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в выражениях EXISTS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsSubqueriesInExists()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsSubqueriesInExists указывается с помощью метода supportsSubqueriesInExists в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
