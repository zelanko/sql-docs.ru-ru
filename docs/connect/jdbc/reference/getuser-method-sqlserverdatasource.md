---
title: Метод SQLServerDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5562f9b19b59096784ad3dd2a09e9135a7e07cf2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978183"
---
# <a name="getuser-method-sqlserverdatasource"></a>Метод getUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя пользователя, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее имя пользователя.  
  
## <a name="remarks"></a>Remarks  
 Метод [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) задает имя пользователя, которое будет использоваться при подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если значение имени пользователя не задано, метод getUser возвращает значение NULL по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
