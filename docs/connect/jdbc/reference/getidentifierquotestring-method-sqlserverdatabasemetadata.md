---
title: Метод getIdentifierQuoteString (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIdentifierQuoteString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dea35a0-56a8-412c-8cd3-6539527ff597
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe27259efbc3448fd0d8d4350d0c2e93e906c34a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982851"
---
# <a name="getidentifierquotestring-method-sqlserverdatabasemetadata"></a>Метод getIdentifierQuoteString (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение типа **String**, используемое для заключения в кавычки идентификаторов SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getIdentifierQuoteString()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее идентификаторы в кавычках.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getIdentifierQuoteString задается с помощью метода getIdentifierQuoteString в интерфейсе java.sql.DatabaseMetaData.  
  
 Если драйвер [!INCLUDE[msCoName](../../../includes/msconame_md.md)] JDBC используется с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то этот метод возвращает **двойные кавычки** ("").  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
