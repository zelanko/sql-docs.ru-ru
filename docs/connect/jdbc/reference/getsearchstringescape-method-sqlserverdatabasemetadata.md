---
title: Метод getSearchStringEscape (SQLServerDatabaseMetaData) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9af605053c52c273b45bbc9716e7995a30ada37e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>Метод getSearchStringEscape (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает **строка** , может использоваться для экранирования символов-шаблонов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий шаблон escape-символ строки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSearchStringEscape указывается с помощью метода getSearchStringEscape в интерфейсе java.sql.DatabaseMetaData.  
  
 Этот метод используется только для поиска по шаблону в метаданных. Возвращает «\\». Объект **строка** шаблона поиска можно экранировать символы-шаблоны («%» и «_») и предоставить их как литералы, добавляя в начало обратной косой черты. Это означает "\\%» в «[%]» и «\\\_» для» [\_]».  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
