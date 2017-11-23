---
title: "Выполнение транзакций с драйвером JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 63dbf73c8100c1d4ab12ab80f1e7b6dcf6a5a6fa
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Выполнение транзакций с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Обработка транзакций обязательна для всех приложений, в которых должна гарантироваться согласованность сохраненных данных. С [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], обработка транзакций можно вести в локальной или распределенной. Транзакции — это атомарные согласованные изолированные и устойчивые (ACID) модули исполнения.  
  
 Здесь представлены разделы, в которых описана поддержка транзакций драйвером JDBC, в том числе уровни изоляции, точки сохранения транзакции и удержание результирующего набора.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основные сведения о транзакциях](../../connect/jdbc/understanding-transactions.md)|Общие сведения о работе с транзакциями с помощью драйвера JDBC.|  
|[Основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md)|Общие сведения о работе с транзакциями ХА с помощью драйвера JDBC.|  
|[Основные сведения об уровнях изоляции](../../connect/jdbc/understanding-isolation-levels.md)|Различные уровни изоляции, поддерживаемые драйвером JDBC.|  
|[Использование точек сохранения](../../connect/jdbc/using-savepoints.md)|Использование драйвера JDBC с точками сохранения транзакций.|  
|[Использование возможности ожидания](../../connect/jdbc/using-holdability.md)|Использование драйвера JDBC с удержанием результирующего набора.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
