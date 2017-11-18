---
title: "Метод setServerName (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2efdbb68c0d546776b7027c9130e7589c92322ea
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setservername-method-sqlserverdatasource"></a>Метод setServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя сервера*  
  
 Объект **строка** , содержащее имя сервера.  
  
## <a name="remarks"></a>Замечания  
 Имя сервера — имя узла целевого компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Если не указано свойство serverName, [getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) возвращает значение по умолчанию null.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

