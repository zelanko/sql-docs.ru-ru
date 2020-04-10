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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac38e670cbb0aae3d18e3f066440ba1a81491830
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927262"
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
  
  
