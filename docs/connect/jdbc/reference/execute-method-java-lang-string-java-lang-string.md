---
title: Метод execute (java.lang.String, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (java.lang.String.java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9451c7c2-4c0d-4d1e-9b42-a26ff28e3f6a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 20b8c20feb8c71e192edfedb7d7dda5b549e8469
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801676"
---
# <a name="execute-method-javalangstring-javalangstring"></a>Метод execute (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL, которая может вернуть несколько результатов, и уведомляет [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] о том, что автоматически сформированные ключи, отмеченные в указанном массиве, должны быть доступны для получения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final boolean execute(java.lang.String sql,  
                             java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
 *columnNames*  
  
 Массив строк, которые указывают имена столбцов автоматически формируемых ключей, которые должны быть доступными.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если первый результат является результирующим набором. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод execute определен с помощью метода execute в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод Execute &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
