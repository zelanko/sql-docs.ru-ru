---
title: Метод executeUpdate (java.lang.String, int[]) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String, int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b3d5b60-4285-4047-b13e-106754ca0d98
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a2d0bea512c6cbfda5c283af793365e8aeec590c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786591"
---
# <a name="executeupdate-method-javalangstring-int"></a>Метод executeUpdate (java.lang.String, int[])
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и сообщает [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] о доступности автоматически сформированных ключей, указанных в заданном массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               int[] columnIndexes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
 *columnIndexes*  
  
 Массив значений int, указывающих индексы столбцов автоматически сформированных ключей, которые должны быть доступными.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее либо число обработанных строк, либо значение 0 для инструкций языка DDL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод executeUpdate указывается с помощью метода executeUpdate в интерфейсе java.sql.Statement.  
  
 Если в результате выполнения хранимой процедуры счетчик обновлений больше единицы либо сформировано больше одного результирующего набора, используйте для выполнения хранимой процедуры метод [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод executeUpdate &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
