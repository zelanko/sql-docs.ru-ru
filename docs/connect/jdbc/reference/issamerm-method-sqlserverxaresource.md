---
title: Метод isSameRM (SQLServerXAResource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.isSameRM
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa24c46-b7cf-470a-afa1-52301847a448
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4628f760dadc6619e2ebc3fca5437bc15bf7681
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925066"
---
# <a name="issamerm-method-sqlserverxaresource"></a>Метод isSameRM (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Определяет, совпадает ли экземпляр диспетчера ресурсов, представленный целевым объектом, с экземпляром диспетчера ресурсов, представленным заданным объектом XAResource.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isSameRM(javax.transaction.xa.XAResource xares)  
```  
  
#### <a name="parameters"></a>Параметры  
 *xares*  
  
 Объект XAResource.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если экземпляры совпадают. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Этот метод commit определен с помощью метода commit в интерфейсе javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
