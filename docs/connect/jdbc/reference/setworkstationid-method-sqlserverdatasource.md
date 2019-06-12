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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3b9b4dd4ce34dcc39148a2346fd729a8dfb6b87f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773215"
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
 Идентификатор workstationID — это имя клиентского компьютера или рабочей станции. Если свойство workstationID не задано, значение по умолчанию создается путем вызова метода InetAddress.getLocalHost().getHostName(). Если getHostName возвращает пустое значение, вызывается метод getHostAddress().toString().  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
