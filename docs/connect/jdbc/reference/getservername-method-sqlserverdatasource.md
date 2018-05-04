---
title: Метод getServerName (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f52990aa15bc059c1da3b34e203a9bea1ccaf0f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
