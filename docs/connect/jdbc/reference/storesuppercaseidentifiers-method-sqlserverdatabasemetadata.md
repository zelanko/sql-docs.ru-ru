---
description: Метод storesUpperCaseIdentifiers (SQLServerDatabaseMetaData)
title: Метод storesUpperCaseIdentifiers | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesUpperCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a622b748-d10b-4f02-afe3-fba4a5bca17b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e435ca2947dec04a0c9568389150f7f45082333f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450416"
---
# <a name="storesuppercaseidentifiers-method-sqlserverdatabasemetadata"></a>Метод storesUpperCaseIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет их в верхнем регистре.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean storesUpperCaseIdentifiers()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если идентификаторы хранятся в верхнем регистре. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод storesUpperCaseIdentifiers задается с помощью метода storesUpperCaseIdentifiers в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
