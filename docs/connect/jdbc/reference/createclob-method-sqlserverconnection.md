---
title: Метод createClob (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 291016047ab29d4e563e2a7248c4cd4624669ef9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927705"
---
# <a name="createclob-method-sqlserverconnection"></a>Метод createClob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект Clob, не содержащий данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Clob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод createClob задается с помощью метода createClob в интерфейсе java.sql.Connection.  
  
 Этот метод избавляет от необходимости использовать [конструктор SQLServerClob (SQLServerConnection, java.lang.String)](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
