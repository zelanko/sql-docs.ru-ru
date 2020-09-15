---
description: Метод setClientInfo (java.util.Properties)
title: Метод setClientInfo (java.util.Properties) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44c70b1f1a8bd88065ecee03cb85aa0ed7502208
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432196"
---
# <a name="setclientinfo-method-javautilproperties"></a>Метод setClientInfo (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение свойств сведений о клиенте для соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Параметры  
 *properties*  
  
 Объект Properties, содержащий список задаваемых свойств сведений о клиенте.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setClientInfo задается с помощью метода setClientInfo в интерфейсе java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не поддерживает свойства сведений о клиенте. Этот метод создает предупреждения, если входной параметр *properties* не ссылается на пустой набор свойств. Другими словами, этот метод формирует предупреждения для свойств, которые нужно задать в приложении. Приложения должны использовать метод [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) класса [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) для извлечения каждого предупреждения.  
  
## <a name="see-also"></a>См. также:  
 [Метод setClientInfo (SQLServerConnection)](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
