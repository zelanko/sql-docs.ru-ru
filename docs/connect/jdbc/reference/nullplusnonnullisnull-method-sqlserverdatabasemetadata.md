---
description: Метод nullPlusNonNullIsNull (SQLServerDatabaseMetaData)
title: Метод nullPlusNonNullIsNull (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.nullPlusNonNullIsNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c594736f-3a9b-463f-bbd8-eaf9221230ea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92ee7fe72d95984a65eb666f9685f1512a9ad3c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433176"
---
# <a name="nullplusnonnullisnull-method-sqlserverdatabasemetadata"></a>Метод nullPlusNonNullIsNull (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, поддерживает ли эта база данных получение значений NULL в результате объединения значений NULL и значений, отличных от NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean nullPlusNonNullIsNull()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если поддерживается объединение значений. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод nullPlusNonNullIsNull задается с помощью метода nullPlusNonNullIsNull в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
