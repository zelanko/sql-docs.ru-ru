---
description: Метод getWarnings (SQLServerResultSet)
title: Метод getWarnings (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb4339b0-383b-4337-a935-e8ec3f0d4123
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 74d18c8739a61b15fbbc7fb9606a211cae62f32b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433796"
---
# <a name="getwarnings-method-sqlserverresultset"></a>Метод getWarnings (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает первое предупреждение, указанное в отчетах для вызовов этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  Сейчас этот метод не поддерживается [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При вызове этот метод всегда возвращает значение NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.SQLWarning getWarnings()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLWarning.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getWarnings задается с помощью метода getWarnings в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
