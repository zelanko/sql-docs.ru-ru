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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 231811818c5a733f0224465e93739f7fee96f9de
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924822"
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
  
  
