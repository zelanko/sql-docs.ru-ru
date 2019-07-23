---
title: Метод Recover (SQLServerXAResource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 92d7b0db997a6b77b43efb6d8104f629bb5507e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976020"
---
# <a name="recover-method-sqlserverxaresource"></a>Метод recover (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает список ветвей подготовленной транзакции от диспетчера ресурсов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Параметры  
 *flags*  
  
 Значение **типа int** , которое может принимать одно из следующих значений: XARESOURCE. Тмстартрскан или XARESOURCE. Тмендрскан или XARESOURCE. Тмнофлагс или XARESOURCE. тмстарттрскан | XAResource. ТМЕНДРСКАН.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Xid.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Этот метод recover определен с помощью метода recover в интерфейсе javax.transaction.xa.XAResource.  
  
 Если **флаг** параметра не XARESOURCE. Тмстартрскан или XARESOURCE. тмстартрскан | XAResource. ТМЕНДРСКАН, должно быть выполнено сканирование восстановления.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
