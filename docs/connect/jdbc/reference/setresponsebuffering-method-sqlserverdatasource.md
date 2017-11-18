---
title: "Метод setResponseBuffering (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 88cfa89a30461ba3013c7b227651d5d0292c77b2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>Метод setResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает режим буферизации ответов для подключений, созданных с помощью этого [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *value*  
  
 Объект **строка** , содержащий режим буферизации и потоковой передачи. Допустимый режим может принимать одно из следующих строк без учета регистра: **полного** или **адаптивной**.  
  
## <a name="remarks"></a>Замечания  
 **Полного** значение указывает на чтение всех результатов с сервера во время выполнения.  
  
 **Адаптивной** значение указывает на буферизацию минимума данных при необходимости. **Адаптивной** значение — режим буферизации по умолчанию.  
  
 Дополнительные сведения об использовании режима буферизации ответов см. в разделе [с помощью адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

