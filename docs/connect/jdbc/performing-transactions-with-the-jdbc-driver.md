---
title: Выполнение транзакций с драйвером JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8471493fb68df8369084046075f88a1e7b4f2e3e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794095"
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Выполнение транзакций с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Обработка транзакций обязательна для всех приложений, в которых должна гарантироваться согласованность сохраненных данных. С помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] обработку транзакций можно вести в локальной или распределенной среде. Транзакции — это атомарные согласованные изолированные и устойчивые (ACID) модули исполнения.  
  
 Здесь представлены разделы, в которых описана поддержка транзакций драйвером JDBC, в том числе уровни изоляции, точки сохранения транзакции и удержание результирующего набора.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основные сведения о транзакциях](../../connect/jdbc/understanding-transactions.md)|Общие сведения о работе с транзакциями с помощью драйвера JDBC.|  
|[Основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md)|Общие сведения о работе с транзакциями ХА с помощью драйвера JDBC.|  
|[Основные сведения об уровнях изоляции](../../connect/jdbc/understanding-isolation-levels.md)|Различные уровни изоляции, поддерживаемые драйвером JDBC.|  
|[Использование точек сохранения](../../connect/jdbc/using-savepoints.md)|Использование драйвера JDBC с точками сохранения транзакций.|  
|[Использование возможности ожидания](../../connect/jdbc/using-holdability.md)|Использование драйвера JDBC с удержанием результирующего набора.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
