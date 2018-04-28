---
title: Метод setFailoverPartner (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c967b155b5db8e015858b6478e29f8bd17801e0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Метод setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя сервера*  
  
 Объект **строка** , содержащее имя сервера отработки отказа.  
  
## <a name="remarks"></a>Замечания  
 Значение, задаваемое этим методом, используется в случае сбоя исходного подключения к основному серверу. После установления исходного подключения это значение не обрабатывается. [SetDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) метод должен также использоваться в сочетании с помощью этого метода или будет вызвано исключение.  
  
 Драйвер не поддерживает задание номера порта для сервера отработки отказа, когда задается имя сервера отработки отказа. Однако, при вызове [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) метод и [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) метод с [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) метод поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
