---
title: Метод addBatch (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.addBatch (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 093f6c3b-49a6-4043-9993-bd0482de04dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 42045bee1dca5d2a9c5fc748f5d7a1c5ebbca9de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956014"
---
# <a name="addbatch-method-javalangstring"></a>Метод addBatch (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Добавляет заданную команду SQL в текущий список команд для этого объекта [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод addBatch задается методом addBatch в интерфейсе Java. SQL. Statement.  
  
 Вызов этого метода приводит к исключению, поскольку инструкция SQL для объекта SQLServerPreparedStatement определена при создании объекта.  
  
## <a name="see-also"></a>См. также:  
 [addBatch метод (SQLServerPreparedStatement)](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
