---
title: Метод setFailoverPartner (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 11bd963275f94fd5ab37d17ead561adbfb0bff5c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802963"
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Метод setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *serverName*  
  
 Значение **String**, содержащее имя сервера отработки отказа.  
  
## <a name="remarks"></a>Remarks  
 Значение, задаваемое этим методом, используется в случае сбоя исходного подключения к основному серверу. После установления исходного подключения это значение не обрабатывается. Совместно с этим методом также следует использовать метод [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md). В противном случае будет вызываться исключение.  
  
 Драйвер не поддерживает задание номера порта для сервера отработки отказа, когда задается имя сервера отработки отказа. Однако поддерживается вызов метода [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) и метода [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) с методом [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
