---
description: Метод getServerName (SQLServerDataSource)
title: Метод getServerName (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f8e2045d2c296386f13907ce3b95923a5b58826e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434606"
---
# <a name="getservername-method-sqlserverdatasource"></a>Метод getServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее имя сервера, или значение NULL, если значение не задано.  
  
## <a name="remarks"></a>Remarks  
 Именем сервера является имя узла целевого компьютера, где работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если свойство getServerName не задано, то метод getServerName возвращает значение NULL по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
