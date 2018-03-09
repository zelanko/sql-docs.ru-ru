---
title: "Метод getServerName (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.getServerName
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2302fded14543647060ce8ddcff4b59e0911c942
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getservername-method-sqlserverdatasource"></a>Метод getServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий имя сервера или значение null, если значение не задано.  
  
## <a name="remarks"></a>Замечания  
 Имя сервера — имя узла целевого компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Если свойство getServerName не задано, то метод getServerName возвращает значение по умолчанию null.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
