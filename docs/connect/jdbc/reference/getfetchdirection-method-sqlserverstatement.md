---
title: Метод getFetchDirection (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1be44732bb2843e7ce4b306a28dec7343d960ea1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983237"
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>Метод getFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает направление выборки строк из таблиц базы данных, заданное по умолчанию для результирующих наборов, созданных на основе объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
> [!NOTE]  
>  В настоящее время этот метод не реализуется драйвером [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Поэтому он всегда будет возвращать FETCH_UNKNOWN.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее на направление выборки, указанное методом [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFetchDirection задается с помощью метода getFetchDirection в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
