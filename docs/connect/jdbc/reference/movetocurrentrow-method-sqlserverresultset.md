---
title: Метод moveToCurrentRow (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f0b3e779dd7d3164b8c9277a3d3437137827da6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779592"
---
# <a name="movetocurrentrow-method-sqlserverresultset"></a>Метод moveToCurrentRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор в сохраненное местоположение курсора, то есть обычно в текущую строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void moveToCurrentRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод moveToCurrentRow указывается с помощью метода moveToCurrentRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не выполняет никаких действий, если курсор не находится в строке вставки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
