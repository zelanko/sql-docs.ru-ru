---
title: Конструктор SQLServerClob (SQLServerConnection, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a454567f031d935b6bfcdd8d5d32a6d2bead380f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803142"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>Конструктор SQLServerClob (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр класса [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md) по заданному объекту [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) и строке данных.  
  
> [!NOTE]  
>  Этот метод устарел в версии драйвера JDBC 2.0. Вместо этого используйте метод [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) класса [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Параметры  
 *connection*  
  
 Объект SQLServerConnection.  
  
 *data*  
  
 Данные CLOB.  
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
