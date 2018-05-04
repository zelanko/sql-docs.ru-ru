---
title: Метод getMaxProcedureNameLength (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.getMaxProcedureNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1c05eb3-8465-46fd-99bc-5e8effcafee5
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f652f93f68a6ba63eabc52a731342ed371bef195
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getmaxprocedurenamelength-method-sqlserverdatabasemetadata"></a>Метод getMaxProcedureNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число символов, допустимое в имени процедуры для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMaxProcedureNameLength()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее максимально допустимое число символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getMaxProcedureNameLength указывается с помощью метода getMaxProcedureNameLength в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
