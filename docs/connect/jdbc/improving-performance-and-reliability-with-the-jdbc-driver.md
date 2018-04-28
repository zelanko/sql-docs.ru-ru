---
title: Повышение производительности и надежности с помощью драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9333af182b7d4fdd8edfe983a6b3874845ba979
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Повышение производительности и надежности с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Одна из сторон разработки приложений, характерная для всех приложений — постоянная необходимость улучшения производительности и надежности. Существует несколько способов достижения данных целей при использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 В подразделах данного раздела приводится описание различных способов улучшения производительности и надежности приложения при использовании драйвера JDBC.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Закрытие неиспользуемых объектов](../../connect/jdbc/closing-objects-when-not-in-use.md)|Описывается важность закрытия объектов драйвера JDBC, когда в них больше нет необходимости.|  
|[Управление размером транзакции](../../connect/jdbc/managing-transaction-size.md)|Описываются способы улучшения производительности транзакций.|  
|[Работа с инструкциями и результирующими наборами](../../connect/jdbc/working-with-statements-and-result-sets.md)|Описываются способы улучшения производительности при работе с объектами инструкции или результирующего набора.|  
|[Использование адаптивной буферизации](../../connect/jdbc/using-adaptive-buffering.md)|Описывается функция адаптивной буферизации, разработанная для получения любых данных большого объема и позволяющая избежать излишней нагрузки, связанной с использованием серверных курсоров.|  
|[Разреженные столбцы](../../connect/jdbc/sparse-columns.md)|Обсуждение поддержки драйвера JDBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] разреженных столбцов.|  
|[Кэширование метаданных подготовленной инструкции для JDBC Driver](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Описывает способы улучшения производительности с запросами подготовленной инструкции.|
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  