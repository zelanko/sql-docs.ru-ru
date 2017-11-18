---
title: "Метод setApplicationName (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dddba9b465d2b9bd2edfe42f850af6a3b64cd503
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setapplicationname-method-sqlserverdatasource"></a>Метод setApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *applicationName*  
  
 Объект **строка** , содержащее имя приложения.  
  
## <a name="remarks"></a>Замечания  
 Имя приложения используется для идентификации определенных приложений в различных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] профилирования и средства ведения журнала. Если имя приложения не задано, метод getApplicationName возвращает нелокализованную строку «[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]».  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

