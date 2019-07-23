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
ms.openlocfilehash: c36d7980355eed1e1a1e8f42fb53c75fdb70d0ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976956"
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
 Этот метод jdbcCompliant задается методом jdbcCompliant в интерфейсе Java. SQL. Driver.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Элементы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Класс SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
