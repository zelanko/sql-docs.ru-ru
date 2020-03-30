---
title: Метод cancel (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.cancel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04f3461743801e69248362710197ce2d4c31384f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955785"
---
# <a name="cancel-method-sqlserverstatement"></a>Метод cancel (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Отменяет инструкцию SQL, выполняемую в настоящее время объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void cancel()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод cancel определен с помощью метода cancel в интерфейсе java.sql.ResultSet.  
  
 При выполнении инструкции, создающей крупный однопроходный результирующий набор, доступный только для чтения, реальный интерес могут представлять только первые несколько строк возвращаемого набора. В этом случае приложение может вызвать метод [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) связанного объекта инструкции до закрытия результирующего набора, чтобы уменьшить время обработки, необходимое для удаления оставшихся лишних строк. Чтобы определить целесообразность применения этого метода, рекомендуется сравнить достигаемый выигрыш во времени обработки со временем, расходуемым на дополнительное обращение к серверу для отмены выполнения.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
