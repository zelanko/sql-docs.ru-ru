---
title: Метод setWorkstationID (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2c7664cb50f25d429ee74a163c589436bacf8902
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901600"
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>Метод setWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя клиентского компьютера, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Параметры  
 *workstationID*  
  
 Значение **String**, содержащее имя клиентского компьютера.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор workstationID — это имя клиентского компьютера или рабочей станции. Если свойство workstationID не задано, то значение по умолчанию создается путем вызова метода InetAddress.getLocalHost().getHostName(). Если getHostName возвращает пустое значение, вызывается метод getHostAddress().toString().  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
