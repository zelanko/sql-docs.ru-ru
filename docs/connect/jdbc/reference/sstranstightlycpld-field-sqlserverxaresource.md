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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6d816ba896b792894716b9b61b133d1acea0c93
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925643"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Поле SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Используется для разрешения тесно связанных транзакций XA, имеющих различные идентификаторы ветвей транзакции (XID), но одинаковые глобальные идентификаторы транзакции (GTRID).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Значение поля  
 Значение **int** для 32768.  
  
## <a name="remarks"></a>Remarks  
 Каждая транзакция определяется по идентификатору ветви транзакции (XID) и глобальному идентификатору транзакции (GTRID). Чтобы разрешить приложениям использовать тесно связанные транзакции XA, имеющие различные идентификаторы XID, но одинаковые идентификаторы GTRID, необходимо задать значение [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) в параметре flags метода XAResource.start. См. сведения об использовании флага в руководстве по [выполнению транзакций XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>См. также:  
 [Поля SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
