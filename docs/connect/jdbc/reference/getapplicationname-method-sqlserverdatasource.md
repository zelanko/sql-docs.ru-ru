---
title: "Метод getApplicationName (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4ce2cfbae2a65b0d6f0e2ede30559e485bf5e207
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getapplicationname-method-sqlserverdatasource"></a>Метод getApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее имя приложения или «[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]», если значение не задано.  
  
## <a name="remarks"></a>Замечания  
 Имя приложения используется для идентификации определенных приложений в различных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] профилирования и средства ведения журнала. Если имя приложения не задано, метод getApplicationName возвращает нелокализованную строку «[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]».  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

