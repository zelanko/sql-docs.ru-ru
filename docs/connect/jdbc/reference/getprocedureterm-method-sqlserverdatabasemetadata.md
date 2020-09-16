---
description: Метод getProcedureTerm (SQLServerDatabaseMetaData)
title: Метод getProcedureTerm (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedureTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3336d4c1-d999-43cc-b36b-ff1532e899bc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39564dfb9f802564805a5fbe58115a883551ca20
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434936"
---
# <a name="getprocedureterm-method-sqlserverdatabasemetadata"></a>Метод getProcedureTerm (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает предпочтительный термин для процедуры в этой базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getProcedureTerm()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее термин для процедуры.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getProcedureTerm задается с помощью метода getProcedureTerm в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
