---
title: Метод getLockTimeout (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f01072360ecb2a917527b589d9762e5764fef0e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>Метод getLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **int** значение, указывающее число миллисекунд, базы данных будет ожидать до появления сообщения о времени ожидания блокировки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение, содержащее число миллисекунд, база данных.  
  
## <a name="remarks"></a>Замечания  
 Время ожидания блокировки — это продолжительность времени (в миллисекундах) до того, как база данных сообщает об истечении времени ожидания блокировки. Значение -1 (задано по умолчанию) показывает, что время ожидания неограниченно. Если задано это значение, оно будет использоваться по умолчанию для всех инструкций в соединении.  
  
> [!NOTE]  
>  Значение 0 указывает на отсутствие ожидания. Если свойство lockTimeout не задано, то метод getLockTimeout возвращает значение по умолчанию (-1).  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
