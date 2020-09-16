---
description: Метод jdbcCompliant (SQLServerDriver)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25495005dafdc95982b2f7005c96eb186c864caf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433286"
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
 Этот метод jdbcCompliant задается с помощью метода jdbcCompliant в интерфейсе java.sql.Driver.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Элементы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Класс SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
