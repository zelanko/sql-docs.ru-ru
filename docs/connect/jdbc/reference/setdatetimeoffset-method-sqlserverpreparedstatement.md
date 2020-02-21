---
title: Метод setDateTimeOffset (SQLServerPreparedStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5014dba9-1755-4769-b070-6cbeecee864e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 429e1720a6fac8c01ce2d201717787146bc8cc63
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974361"
---
# <a name="setdatetimeoffset-method-sqlserverpreparedstatement"></a>Метод setDateTimeOffset (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Задает для указанного столбца значение [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setDateTimeOffset(int n, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 Порядковый номер столбца (начиная с нуля).  
  
 *x*  
  
 Объект [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
