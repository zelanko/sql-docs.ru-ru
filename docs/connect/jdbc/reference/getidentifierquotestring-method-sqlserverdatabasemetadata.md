---
title: Метод getIdentifierQuoteString (SQLServerDatabaseMetaData) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 99044bb6a9536f7ad2d2fe69284e4699786e6593
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774455"
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
 Этот метод getIdentifierQuoteString указывается с помощью метода getIdentifierQuoteString в интерфейсе java.sql.DatabaseMetaData.  
  
 Если драйвер [!INCLUDE[msCoName](../../../includes/msconame_md.md)] JDBC используется с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то этот метод возвращает **двойные кавычки** ("").  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
