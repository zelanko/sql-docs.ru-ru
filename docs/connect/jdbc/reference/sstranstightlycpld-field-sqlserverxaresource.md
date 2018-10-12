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
manager: craigg
ms.openlocfilehash: 8129cf30a7ba95c39281c9ff4bd2a5c0eac4183c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818422"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Поле SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Используется для разрешения тесно связанных транзакций XA, имеющих различные идентификаторы ветвей транзакции (XID), но одинаковые глобальные идентификаторы транзакции (GTRID).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Значение поля  
 **Int** значение 32768 типа.  
  
## <a name="remarks"></a>Remarks  
 Каждая транзакция определяется по идентификатору ветви транзакции (XID) и глобальному идентификатору транзакции (GTRID). Чтобы разрешить приложениям использовать тесно связанные транзакции XA, имеющие различные идентификаторы XID, но одинаковые идентификаторы GTRID, необходимо задать значение [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) в параметре flags метода XAResource.start. Дополнительные сведения об использовании этого флага см. в разделе [основные сведения о транзакциях XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>См. также:  
 [Поля SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
