---
title: "Метод getURL (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dd0d5d2c-91fe-4b0f-a162-69d898ba176e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d0ea89d9dab71fcc1572ad6113a76aa2f5face79
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="geturl-method-sqlserverdatasource"></a>Метод getURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает URL-адрес, используемый для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий URL-адрес.  
  
## <a name="remarks"></a>Замечания  
 По соображениям безопасности не следует включать пароль в URL-адрес, который предоставляется [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) метод. Так происходит из-за того, что на серверах приложений Java сторонних разработчиков в пользовательском интерфейсе настройки для источника данных часто выводится значение, заданное для свойства URL-адреса. Вместо этого используйте [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) метод, чтобы задать значение пароля. На серверах приложений Java не отображается пароль, заданный в источнике данных в пользовательском интерфейсе настройки.  
  
> [!NOTE]  
>  Если метод setURL не вызывается перед вызовом метода getURL, getURL возвращает значение по умолчанию «jdbc:sqlserver: / /».  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
