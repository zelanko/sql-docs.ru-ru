---
title: Метод getClientInfoProperties (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bf9c0696c2169ee9b0dd1af198fcb50333c5d9ca
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66763771"
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
  
## <a name="remarks"></a>Remarks  
 Этот метод getClientInfoProperties указывается с помощью метода getClientInfoProperties в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  Этот метод возвращает пустой результирующий набор. Драйвер поддерживает только параметр **applicationName** и задает **applicationName** только во время соединения. SQL Server не поддерживает обновление данных клиентских приложений после выполнения соединения.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
