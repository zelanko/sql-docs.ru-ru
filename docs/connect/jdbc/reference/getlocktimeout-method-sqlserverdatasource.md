---
title: Метод getLockTimeout (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 120a90168d46f81d57115812c832c5c6674cf436
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66793212"
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>Метод getLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение **int**, указывающее время в миллисекундах, по истечении которого база данных сообщает об истечении времени ожидания блокировки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое содержит число миллисекунд ожидания для базы данных.  
  
## <a name="remarks"></a>Remarks  
 Время ожидания блокировки — это продолжительность времени (в миллисекундах) до того, как база данных сообщит об истечении времени ожидания блокировки. Значение -1 (задано по умолчанию) показывает, что время ожидания не ограничено. Если задано это значение, оно будет использоваться по умолчанию для всех инструкций в соединении.  
  
> [!NOTE]  
>  Значение 0 указывает на отсутствие ожидания. Если свойство lockTimeout не задано, то метод getLockTimeout возвращает значение по умолчанию (-1).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
