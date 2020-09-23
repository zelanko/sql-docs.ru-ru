---
description: Метод setObject (int, java.lang.Object)
title: Метод setObject (int, java.lang.Object) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4889cde1e7c50cb9aeb40d05468c035b99772a72
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458576"
---
# <a name="setobject-method-int-javalangobject"></a>Метод setObject (int, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает значение указанного параметра по заданному объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение **int**, определяющее номер параметра.  
  
 *obj*  
  
 Объект.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод setObject определен с помощью метода setObject в интерфейсе java.sql.PreparedStatement.  
  
 Перед вызовом метода setObject приложение может задать указанный параметр одним из следующих способов:  
  
-   Методы \<Type> класса SQLServerPreparedStatement или SQLServerCallableStatement.  
  
-   Методы setNull класса SQLServerPreparedStatement или SQLServerCallableStatement.  
  
-   Метод [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) из класса SQLServerCallableStatement  
  
 В этом случае тип параметра задается автоматически. Если приложение вызывает этот метод setObject со значением obj, равным NULL, то драйвер предполагает, что параметр имеет тип, который задан вызванным ранее методом.  
  
 Если значение obj равно NULL и не удается определить сведения о типе для этого параметра, то этот метод setObject преобразует указанный параметр в тип CHAR перед отправкой в базу данных.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 на работу этого метода влияет свойство подключения **sendTimeAsDatetime** ([Настройка свойств подключения](../../../connect/jdbc/setting-the-connection-properties.md)) и [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 См. сведения о [настройке способа отправки значений java.sql.Time на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setObject (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
