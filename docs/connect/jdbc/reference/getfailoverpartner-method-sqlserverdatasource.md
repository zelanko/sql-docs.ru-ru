---
title: Метод getFailoverPartner (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39195742d8b6a2a03b0b2c835f47d0ba42735791
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730462"
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>Метод getFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее имя участника отработки отказа, или значение NULL, если имя не задано.  
  
## <a name="remarks"></a>Remarks  
 Значение, возвращаемое этим методом, отражает имя участника отработки отказа, заданное методом [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
