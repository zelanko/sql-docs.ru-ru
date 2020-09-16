---
description: Метод finalize (SQLServerResultSet)
title: Метод finalize (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f6f232e7755dd975edaa7b255e5ffe6dd9f85091
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437596"
---
# <a name="finalize-method-sqlserverresultset"></a>Метод finalize (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Явно закрывает этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Remarks  
 Закрывает результирующий набор, если его не закрывает приложение. Этот метод существует только для обеспечения соответствия спецификации JDBC. Поскольку виртуальная машина Java (JVM) не гарантирует выполнения метода завершения, то приложения, которые не закрывают результирующие наборы явно, могут вызвать взаимоблокировку с другой инструкцией, которая использует то же соединение и блокируется на общем серверном ресурсе, например в случае блокировки строк.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
