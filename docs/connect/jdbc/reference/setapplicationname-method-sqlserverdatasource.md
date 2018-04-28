---
title: Метод setApplicationName (SQLServerDataSource) | Документы Microsoft
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8423c6f9307b875821302ae2deb0c0bd60e45be6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>Метод setApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ApplicationName*  
  
 Объект **строка** , содержащее имя приложения.  
  
## <a name="remarks"></a>Замечания  
 Имя приложения используется для идентификации определенных приложений в различных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] профилирования и средства ведения журнала. Если имя приложения не задано, метод getApplicationName возвращает нелокализованную строку «[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]».  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
