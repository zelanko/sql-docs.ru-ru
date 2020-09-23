---
title: Выполнение транзакций с помощью JDBC Driver
description: Сведения о поддержке транзакций, в том числе уровней изоляции, точек сохранения транзакции и удержания результирующего набора, драйвером JDBC для SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff851fc3d62be939eab7983eee80a173160f0d5c
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435407"
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Выполнение транзакций с помощью JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Обработка транзакций обязательна для всех приложений, в которых должна гарантироваться согласованность сохраненных данных. С помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] обработку транзакций можно вести в локальной или распределенной среде. Транзакции — это атомарные согласованные изолированные и устойчивые (ACID) модули исполнения.  
  
 Здесь представлены разделы, в которых описана поддержка транзакций драйвером JDBC, в том числе уровни изоляции, точки сохранения транзакции и удержание результирующего набора.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основные сведения о транзакциях](../../connect/jdbc/understanding-transactions.md)|Общие сведения о работе с транзакциями с помощью драйвера JDBC.|  
|[Основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md)|Общие сведения о работе с транзакциями ХА с помощью драйвера JDBC.|  
|[Основные сведения об уровнях изоляции](../../connect/jdbc/understanding-isolation-levels.md)|Различные уровни изоляции, поддерживаемые драйвером JDBC.|  
|[Использование точек сохранения](../../connect/jdbc/using-savepoints.md)|Использование драйвера JDBC с точками сохранения транзакций.|  
|[Использование возможности ожидания](../../connect/jdbc/using-holdability.md)|Использование драйвера JDBC с удержанием результирующего набора.|  
  
## <a name="see-also"></a>См. также раздел  
 [Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
