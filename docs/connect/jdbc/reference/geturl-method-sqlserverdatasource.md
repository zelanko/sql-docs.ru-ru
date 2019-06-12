---
title: Метод getURL (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dd0d5d2c-91fe-4b0f-a162-69d898ba176e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9c075c9190f8299335b8a1ff55ac81096f726711
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779702"
---
# <a name="geturl-method-sqlserverdatasource"></a>Метод getURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает URL-адрес, используемый для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее URL-адрес.  
  
## <a name="remarks"></a>Remarks  
 По соображениям безопасности не следует включать пароль в URL-адрес, передаваемый в методе [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md). Так происходит из-за того, что на серверах приложений Java сторонних разработчиков в пользовательском интерфейсе настройки для источника данных часто выводится значение, заданное для свойства URL-адреса. Вместо этого используйте для задания значения пароля метод [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md). На серверах приложений Java не отображается пароль, заданный в источнике данных в пользовательском интерфейсе настройки.  
  
> [!NOTE]  
>  Если метод setURL не вызван перед методом getURL, то getURL возвращает значение по умолчанию — "jdbc:sqlserver://".  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
