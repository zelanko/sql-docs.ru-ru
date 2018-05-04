---
title: Конструктор SQLServerClob (SQLServerConnection, java.lang.String) | Документы Microsoft
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
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b6c7982dd0bf12ee7314e6903e455f2bec3e090
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>Конструктор SQLServerClob (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md) класса для заданного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объектов и строку данных.  
  
> [!NOTE]  
>  Этот метод устарел в версии драйвера JDBC 2.0. Вместо этого используйте [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) метод [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Параметры  
 *подключение*  
  
 Объект SQLServerConnection.  
  
 *data*  
  
 Данные CLOB.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
