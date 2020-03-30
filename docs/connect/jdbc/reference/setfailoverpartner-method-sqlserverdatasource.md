---
title: Метод setFailoverPartner (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: 1d152001d1b0eb4ad47936d04ba6c74b8ae7f6e3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974278"
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
  
  
