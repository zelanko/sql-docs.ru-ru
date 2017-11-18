---
title: "Метод setLockTimeout (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4d3801e4494ae42cabc1d3ca149669a66273574
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>Метод setLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **int** значение, указывающее, сколько миллисекунд ждать, пока база данных сообщает об истечении времени ожидания блокировки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *lockTimeout*  
  
 **Int** значение, содержащее число миллисекунд ожидания.  
  
## <a name="remarks"></a>Замечания  
 Время ожидания блокировки — это продолжительность времени (в миллисекундах) до того, как база данных сообщает об истечении времени ожидания блокировки. Значение -1 (задано по умолчанию) показывает, что время ожидания неограниченно. Если задано это значение, оно будет использоваться по умолчанию для всех инструкций в соединении.  
  
> [!NOTE]  
>  Значение 0 указывает на отсутствие ожидания. Если свойство lockTimeout не задано, [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md) метод возвращает значение по умолчанию-1.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

