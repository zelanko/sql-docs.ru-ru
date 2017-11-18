---
title: "Свойства источника данных параметр | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e49d68f567f26e852dcf8bee3a9827797c9c23f2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-data-source-properties"></a>Задание свойств источника данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Источники данных являются предпочтительным механизмом, с помощью которого создаются соединения JDBC на платформе Java в среде Enterprise Edition (Java EE). Источники данных предоставляют соединения, пулы соединений, распределенные соединения, и для этого не нужно использовать жестко запрограммированные свойства соединения на коде Java. Все [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] источники данных можно задать или получить значение любого свойства с помощью соответствующего задания и считывания соответственно.  
  
 Продукты Java EE, например серверы приложений и обработчики сервлетов/JSP, как правило, позволяют настроить источники данных для доступа к базе данных. Все свойства, перечисленные в [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) могут быть заданы там, где конфигурация позволяет вводить свойства в виде свойство = значение пары.  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] источники данных в разделе [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класса. Пример использования класса SQLServerDataSource, чтобы установить соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных см. в разделе [образец источника данных](../../connect/jdbc/data-source-sample.md).  
  
## <a name="see-also"></a>См. также:  
 [Подключение к SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

