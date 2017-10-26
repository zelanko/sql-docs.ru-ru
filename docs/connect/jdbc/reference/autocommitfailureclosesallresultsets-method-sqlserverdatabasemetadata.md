---
title: "Драйвер JDBC закройте открытые результирующие наборы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f2f09f2eacf96ccebb88376ba3866d4188b377d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# Метод autoCommitFailureClosesAllResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, закрывает ли драйвер JDBC все открытые результирующие наборы, включая те, которые допускают удержание, когда при включенном режиме автоматической фиксации возникает исключение.  
  
## Синтаксис  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## Возвращаемое значение  
 **значение true,** в случае, если все открытые привести наборами, включая удерживаемые, закрыты при включенном автоматической фиксации и возникновении исключения. В противном случае — **false**.  
  
## Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Замечания  
 Этот метод autoCommitFailureClosesAllResultSets указывается с помощью метода autoCommitFailureClosesAllResultSets в интерфейсе java.sql.DatabaseMetaData.  
  
## См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

