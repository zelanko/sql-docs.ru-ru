---
title: Метод jdbcCompliant (SQLServerDriver) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9735b94f6b888f3ee83f7c9e807d4d8ecef22cdb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47672852"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>Метод jdbcCompliant (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Проверяет, отвечает ли драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] спецификации для JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если драйвер JDBC отвечает минимальным требованиям. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Этот метод jdbcCompliant указывается в методе jdbcCompliant в интерфейсе java.sql.Driver.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Элементы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Класс SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
