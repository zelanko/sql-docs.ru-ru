---
title: Метод Close (SQLServerResultSet) | Документы Microsoft
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
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: deea90b13bb4bb99c504f5eaa344babdf4a1c680
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="close-method-sqlserverresultset"></a>Метод close (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Это освобождает [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта базы данных и ресурсы JDBC вместо ожидания это может произойти, когда он автоматически закрывается.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод close определяется close-метод в интерфейсе java.sql.ResultSet.  
  
 Автоматически закрывает объект SQLServerResultSet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, который его формирует, когда этот объект SQLServerStatement — закрытые повторного выполнения и используется для получения следующего результата из последовательности множественных результатов . Объект SQLServerResultSet закрыт автоматически после сбора мусора.  
  
 При выполнении инструкции, создающей крупный однопроходный результирующий набор, доступный только для чтения, реальный интерес могут представлять только первые несколько строк возвращаемого набора. В этом случае приложение может вызвать [отменить](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) метод объекта связанные инструкции до закрытия результирующего набора, чтобы уменьшить время обработки, необходимое для удаления оставшихся лишних строк. Чтобы определить целесообразность применения этого метода, рекомендуется сравнить достигаемый выигрыш во времени обработки со временем, расходуемым на дополнительное обращение к серверу для отмены выполнения.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
