---
title: "Метод (SQLServerResultSet) moveToCurrentRow | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8548c196214955e03a04a9a318a30701b0b26f1e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# moveToCurrentRow метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор в сохраненное местоположение курсора, то есть обычно в текущую строку.  
  
## Синтаксис  
  
```  
  
public void moveToCurrentRow()  
```  
  
## Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Замечания  
 Этот метод moveToCurrentRow указывается с помощью метода moveToCurrentRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не выполняет никаких действий, если курсор не находится в строке вставки.  
  
## См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
