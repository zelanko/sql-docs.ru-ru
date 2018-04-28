---
title: Конструктор SQLServerBlob (SQLServerConnection, byte) | Документы Microsoft
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
- SQLServerConnection, byte[].SQLServerBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48b3a3f975f733db124ebcb9e47b7a98b6ec46c8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>Конструктор SQLServerBlob (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md) класса для заданного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта и **байтов** массива.  
  
> [!NOTE]  
>  Этот метод устарел в версии драйвера JDBC 2.0. Вместо этого используйте [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md) метод [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>Параметры  
 *подключение*  
  
 Объект SQLServerConnection.  
  
 *data*  
  
 Объект **байтов** массива.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
