---
title: Метод getNumericFunctions (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getNumericFunctions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8d1c3848-bdb7-452a-862f-6421e1a7ce8b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e6b38d58ddf81f0b8439912b865b1d94a7b15ecf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67981273"
---
# <a name="getnumericfunctions-method-sqlserverdatabasemetadata"></a>Метод getNumericFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает список с разделителями-запятыми математических функций, доступных для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getNumericFunctions()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее доступные математические функции.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getNumericFunctions определен с помощью метода getNumericFunctions в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
