---
title: Соединение и извлечение данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 049b3cbc3a5ddebd30aa111f7c3bd62d46360f43
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828867"
---
# <a name="connecting-and-retrieving-data"></a>Соединение и извлечение данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При работе с [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], существует два основных способа подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Один — задать свойства подключения в URL-АДРЕСЕ соединения и вызова метода getConnection для возвращения класса DriverManager [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
> [!NOTE]  
>  Список свойств соединения, поддерживаемых драйвером JDBC см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Второй метод включает в себя задание свойств соединения с помощью методов задания [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класса и затем вызвать [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) метод для возврата SQLServerConnection объект.  
  
 Подразделы этого раздела описываются различные способы, в которой вы можете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, а также демонстрируются различные методики извлечения данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Пример URL-адреса подключения](../../connect/jdbc/connection-url-sample.md)|Описывает, как использовать URL-адрес подключения для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и затем использовать инструкцию SQL для получения данных.|  
|[Пример источника данных](../../connect/jdbc/data-source-sample.md)|Описывается порядок использования источника данных для соединения с SQL Server и последующего использования хранимой процедуры для извлечения данных.|  
  
## <a name="see-also"></a>См. также  
 [Пример приложений драйвера JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
