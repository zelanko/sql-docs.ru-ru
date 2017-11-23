---
title: "Конструктор SQLServerBlob (SQLServerConnection, byte) | Документы Microsoft"
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
apiname: SQLServerConnection, byte[].SQLServerBlob
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b75ad63c8bbf1a928c8a464b3997713f4a6e582e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
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
  
 *данные*  
  
 Объект **байтов** массива.  
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
