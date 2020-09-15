---
description: Метод setLockTimeout (SQLServerDataSource)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37b43e351f2b44ed4376acb60150bca0eed516ea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431746"
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
  
  
