---
title: Метод getClientInfo (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b9fd6139a7fc36033c33fa4fc5301f5f7d0a4f14
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66763928"
---
# <a name="getclientinfo-method-javalangstring"></a>Метод getClientInfo (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение указанного свойства данных клиента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Параметры  
 *name*  
  
 Строка, которая содержит имя извлекаемого свойства сведений о клиенте.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Строка, которая содержит значение свойства сведений о клиенте.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getClientInfo указывается с помощью метода getClientInfo в интерфейсе java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не поддерживает свойства сведений о клиенте. В результате этот метод возвращает значение **null**.  
  
 Аналогичным образом приложения могут использовать метод [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) класса [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) для получения списка свойств сведений о клиенте, поддерживаемых драйвером. Метод [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) возвращает пустой результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Метод getClientInfo (SQLServerConnection)](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
