---
description: Метод getFetchDirection (SQLServerStatement)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2c42f7296f9bb4ac9cffd68f0d13d5ba7ca920c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436046"
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
  
  
