---
title: Метод setLockTimeout (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 95dc93b8695f9bfe464545ab5f1aa6096a4476be
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974110"
---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>Метод setLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение **int**, указывающее время в миллисекундах, по истечении которого база данных сообщает об истечении времени ожидания блокировки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *lockTimeout*  
  
 Значение **int**, содержащее число миллисекунд ожидания.  
  
## <a name="remarks"></a>Remarks  
 Время ожидания блокировки — это продолжительность времени (в миллисекундах) до того, как база данных сообщит об истечении времени ожидания блокировки. Значение -1 (задано по умолчанию) показывает, что время ожидания не ограничено. Если задано это значение, оно будет использоваться по умолчанию для всех инструкций в соединении.  
  
> [!NOTE]  
>  Значение 0 указывает на отсутствие ожидания. Если свойство lockTimeout не задано, то метод [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md) возвращает значение по умолчанию (-1).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
