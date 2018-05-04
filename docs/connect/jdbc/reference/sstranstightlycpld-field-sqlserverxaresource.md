---
title: Поле SSTRANSTIGHTLYCPLD (SQLServerXAResource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02f95a1ac9a40cad4ce788edbaea064bd11bfd56
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 Каждая транзакция определяется по идентификатору ветви транзакции (XID) и глобальному идентификатору транзакции (GTRID). Чтобы разрешить приложениям использовать тесно связанные транзакции XA, в которых есть другой XID, но же GTRID, необходимо задать [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) в параметре флаги XAResource.start метода. Дополнительные сведения об использовании этого флага см. в разделе [основные сведения о транзакциях XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>См. также  
 [Поля SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
