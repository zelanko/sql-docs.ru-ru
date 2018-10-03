---
title: Конструктор SQLServerBlob (SQLServerConnection, byte) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection, byte[].SQLServerBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a0b33640f9978b5b7b383e7bd89c62e026d5386
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789827"
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>Конструктор SQLServerBlob (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр класса [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md), если имеется объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) и массив **byte**.  
  
> [!NOTE]  
>  Этот метод устарел в версии драйвера JDBC 2.0. Используйте вместо него метод [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md) класса [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>Параметры  
 *connection*  
  
 Объект SQLServerConnection.  
  
 *data*  
  
 Массив **byte**.  
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
