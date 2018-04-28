---
title: Метод setURL (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.setURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea70100-ac98-4625-8748-ef7cc0b111ea
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fefd8718b40dd5ce8528315228ec389c6e5d7de9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="seturl-method-sqlserverdatasource"></a>Метод setURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает URL-адрес, используемый для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Параметры  
 *URL-адрес*  
  
 Объект **строка** , содержащий URL-адрес.  
  
## <a name="remarks"></a>Замечания  
 По соображениям безопасности не следует включать пароль в URL-адрес, передаваемый в метод setURL. Так происходит из-за того, что на серверах приложений Java сторонних разработчиков в пользовательском интерфейсе настройки для источника данных часто выводится значение, заданное для свойства URL-адреса. Вместо этого используйте [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) метод, чтобы задать значение пароля. На серверах приложений Java не отображается пароль, заданный в источнике данных в пользовательском интерфейсе настройки.  
  
> [!NOTE]  
>  Если метод setURL не вызывается перед вызовом метода [getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md) метода getURL возвращает значение по умолчанию «jdbc:sqlserver: / /».  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
