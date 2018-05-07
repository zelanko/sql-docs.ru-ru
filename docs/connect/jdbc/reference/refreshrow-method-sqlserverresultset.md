---
title: Метод refreshRow (SQLServerResultSet) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.refreshRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50d89d95b5aecdd3ae430b278d83ab2222cde7d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="refreshrow-method-sqlserverresultset"></a>Метод refreshRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет текущую строку, записывая последнее значение из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void refreshRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод refreshRow указывается с помощью метода refreshRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не может быть вызван при нахождении курсора в строке вставки.  
  
 Этот метод обеспечивает для приложения способ явно указать драйверу JDBC на необходимость повторного извлечения строк из базы данных. Приложению может потребоваться вызвать этот метод при [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] кэшировании или выполнении повторного извлечения последнего значения строки из базы данных. Если размер выборки больше 1, драйвер JDBC может одновременно обновить несколько строк.  
  
 Все повторно извлеченные значения должны соответствовать уровню изоляции транзакции и чувствительности курсора. Если этот метод вызывается после вызова метода обновления, но перед вызовом метода [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) , обновления, внесенные в строку, теряются. Вызов этого метода, вероятнее всего, приведет к снижению производительности.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
