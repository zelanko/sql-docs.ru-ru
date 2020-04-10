---
title: Метод storesUpperCaseQuotedIdentifiers | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesUpperCaseQuotedIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 936ec140-2597-44e6-82d3-3994a676ee35
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb566a6bbd5a2a5e19a40e284abb4af9a3fd8392
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915630"
---
# <a name="storesuppercasequotedidentifiers-method-sqlserverdatabasemetadata"></a>Метод storesUpperCaseQuotedIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, заключенных в кавычки, и сохраняет их в верхнем регистре.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean storesUpperCaseQuotedIdentifiers()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если идентификаторы хранятся в верхнем регистре. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод storesUpperCaseQuotedIdentifiers указывается с помощью метода storesUpperCaseQuotedIdentifiers в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
