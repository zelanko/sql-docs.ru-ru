---
title: Метод storesLowerCaseIdentifiers (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesLowerCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7dd60f5-c4f3-4b14-9a33-d95327395083
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0c4a376970658df1bdce94e45694edae18149c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67969991"
---
# <a name="storeslowercaseidentifiers-method-sqlserverdatabasemetadata"></a>Метод storesLowerCaseIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет ли их в нижнем регистре.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean storesLowerCaseIdentifiers()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если идентификаторы хранятся в нижнем регистре. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод storesLowerCaseIdentifiers задается методом storesLowerCaseIdentifiers в интерфейсе Java. SQL. DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
