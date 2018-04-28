---
title: Выполнение транзакций с драйвером JDBC | Документы Microsoft
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
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba3c37d70e6457907540abcec19daa275573b414
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Выполнение транзакций с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Обработка транзакций обязательна для всех приложений, в которых должна гарантироваться согласованность сохраненных данных. С [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], обработка транзакций можно вести в локальной или распределенной. Транзакции — это атомарные согласованные изолированные и устойчивые (ACID) модули исполнения.  
  
 Здесь представлены разделы, в которых описана поддержка транзакций драйвером JDBC, в том числе уровни изоляции, точки сохранения транзакции и удержание результирующего набора.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основные сведения о транзакциях](../../connect/jdbc/understanding-transactions.md)|Общие сведения о работе с транзакциями с помощью драйвера JDBC.|  
|[Основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md)|Общие сведения о работе с транзакциями ХА с помощью драйвера JDBC.|  
|[Основные сведения об уровнях изоляции](../../connect/jdbc/understanding-isolation-levels.md)|Различные уровни изоляции, поддерживаемые драйвером JDBC.|  
|[Использование точек сохранения](../../connect/jdbc/using-savepoints.md)|Использование драйвера JDBC с точками сохранения транзакций.|  
|[Использование возможности ожидания](../../connect/jdbc/using-holdability.md)|Использование драйвера JDBC с удержанием результирующего набора.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
