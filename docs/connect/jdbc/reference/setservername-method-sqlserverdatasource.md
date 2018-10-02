---
title: Метод setServerName (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da3aee4570f579e4a3ed6007412222506ed2e24d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827962"
---
# <a name="setservername-method-sqlserverdatasource"></a>Метод setServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя компьютера, на котором работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *serverName*  
  
 Значение типа **String**, содержащее имя сервера.  
  
## <a name="remarks"></a>Remarks  
 Именем сервера является имя узла целевого компьютера, где работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если свойство serverName не задано, то метод [getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) возвращает значение NULL по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
