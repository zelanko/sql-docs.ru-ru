---
title: Метод getCatalogTerm (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0aa5d372-16aa-4790-a8f6-f8b742798f8f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69559cff156c66d7ebbb0bf3675c3c3a455b2e0b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811632"
---
# <a name="getcatalogterm-method-sqlserverdatabasemetadata"></a>Метод getCatalogTerm (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает эквивалент каталога в терминологии поставщика баз данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getCatalogTerm()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее термин каталога.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCatalogTerm указывается с помощью метода getCatalogTerm в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] этот метод всегда будет возвращать термин "database".  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
