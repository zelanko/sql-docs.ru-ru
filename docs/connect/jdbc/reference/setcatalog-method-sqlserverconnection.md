---
title: Метод setCatalog (SQLServerConnection) | Документы Microsoft
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
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0dbb0bbaa8a927ed34bd6d08f96a0f8713f31b94
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setcatalog-method-sqlserverconnection"></a>Метод setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя данного каталога для выбора подпространства это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) базы данных объекта в котором будет производиться работа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Параметры  
 *catalog*  
  
 Объект **строка** , содержащее имя каталога.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setCatalog указывается с помощью метода setCatalog в интерфейсе java.sql.Connection.  
  
 *Каталога* аргумент экранируется драйвером [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] автоматически. С помощью этого метода задает свойство каталога для объекта соединения. Неявным образом это свойство не устанавливается.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
