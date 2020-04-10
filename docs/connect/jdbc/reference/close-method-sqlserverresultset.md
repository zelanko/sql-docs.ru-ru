---
title: Метод close (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8f666ab4b382d14ea64b7fd8638aa0d010ff8ecd
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923623"
---
# <a name="close-method-sqlserverresultset"></a>Метод close (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Высвобождает ресурсы базы данных и JDBC этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) вместо ожидания их автоматического освобождения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод close определяется с помощью метода close в интерфейсе java.sql.ResultSet.  
  
 Объект SQLServerResultSet автоматически закрывается объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), который его формирует, когда объект SQLServerStatement закрывается, выполняется повторно или используется для извлечения следующего результата из последовательности множественных результатов. Объект SQLServerResultSet также автоматически закрывается, когда объект должен быть собран в качестве мусора.  
  
 При выполнении инструкции, создающей крупный однопроходный результирующий набор, доступный только для чтения, реальный интерес могут представлять только первые несколько строк возвращаемого набора. В этом случае приложение может вызвать метод [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) связанного объекта инструкции до закрытия результирующего набора, чтобы уменьшить время обработки, необходимое для удаления оставшихся лишних строк. Чтобы определить целесообразность применения этого метода, рекомендуется сравнить достигаемый выигрыш во времени обработки со временем, расходуемым на дополнительное обращение к серверу для отмены выполнения.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
