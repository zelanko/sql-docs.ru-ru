---
description: Метод createBlob (SQLServerConnection)
title: Метод createBlob (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64a834eee8ced5e60d7f9b834caa41e04b35b6a1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437986"
---
# <a name="createblob-method-sqlserverconnection"></a>Метод createBlob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект BLOB-объект, не содержащий данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Blob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод createBlob задается с помощью метода createBlob в интерфейсе java.sql.Connection.  
  
 Этот метод избавляет от необходимости использовать [конструктор SQLServerBlob (SQLServerConnection, byte)](../../../connect/jdbc/reference/sqlserverblob-constructor-sqlserverconnection-byte.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
