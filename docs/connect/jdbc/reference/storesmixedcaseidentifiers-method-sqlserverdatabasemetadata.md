---
title: Метод storesMixedCaseIdentifiers (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesMixedCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a91e5cd6-22b1-464e-aeec-665590737a74
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a1d1a924b913ecffc4baea959053001d7e30c1db
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67969908"
---
# <a name="storesmixedcaseidentifiers-method-sqlserverdatabasemetadata"></a>Метод storesMixedCaseIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет их в смешанном регистре.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean storesMixedCaseIdentifiers()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если идентификаторы хранятся в смешанном регистре. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод storesMixedCaseIdentifiers задается с помощью метода storesMixedCaseIdentifiers в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
