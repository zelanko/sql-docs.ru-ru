---
title: Поле SSTRANSTIGHTLYCPLD (SQLServerXAResource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36563b76c4207b5924bb32f5c8e99cca575c9d72
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970045"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Поле SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Используется для разрешения тесно связанных транзакций XA, имеющих различные идентификаторы ветвей транзакции (XID), но одинаковые глобальные идентификаторы транзакции (GTRID).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Значение поля  
 Значение **int** , равное 32768.  
  
## <a name="remarks"></a>Remarks  
 Каждая транзакция определяется по идентификатору ветви транзакции (XID) и глобальному идентификатору транзакции (GTRID). Чтобы разрешить приложениям использовать тесно связанные транзакции XA, имеющие различные идентификаторы XID, но одинаковые идентификаторы GTRID, необходимо задать значение [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) в параметре flags метода XAResource.start. Дополнительные сведения об использовании этого флага см. в разделе [основные](../../../connect/jdbc/understanding-xa-transactions.md)сведения о транзакциях XA.  
  
## <a name="see-also"></a>См. также:  
 [Поля SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
