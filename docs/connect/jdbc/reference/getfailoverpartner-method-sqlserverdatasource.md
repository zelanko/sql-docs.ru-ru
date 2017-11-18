---
title: "Метод getFailoverPartner (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f2b5076573d1513313949a5ad9b558a24315bf5c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>Метод getFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее имя участника отработки отказа, или значение null, если не задано.  
  
## <a name="remarks"></a>Замечания  
 Этот метод возвращает значение отражает отказоустойчивого участника имя набора с помощью [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) метод.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

