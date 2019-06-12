---
title: Метод getWarnings (SQLServerResultSet) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e5f58118458d0591d068cedf8a99f389fe00b8f1
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779967"
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
 Этот метод getWarnings указывается с помощью метода getWarnings в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
