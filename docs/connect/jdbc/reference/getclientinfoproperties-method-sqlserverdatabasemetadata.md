---
title: Метод getClientInfoProperties (SQLServerDatabaseMetaData) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e238a9899bd56002d03373ac037b8bd46059b030
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832909"
---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>Метод getClientInfoProperties (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает список свойств данных клиентов, поддерживаемых драйвером.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getClientInfoProperties указывается с помощью метода getClientInfoProperties в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  Этот метод возвращает пустой результирующий набор. Драйвер поддерживает только параметр **applicationName** и задает **applicationName** только во время соединения. SQL Server не поддерживает обновление данных клиентских приложений после выполнения соединения.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
