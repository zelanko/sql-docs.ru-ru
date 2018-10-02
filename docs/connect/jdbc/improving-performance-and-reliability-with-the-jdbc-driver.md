---
title: Использование JDBC Driver для повышения надежности и производительности | Документация Майкрософт
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7650a51e21cd6d1b6a8d4bbacddf6cabdb9cc1e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627912"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Повышение производительности и надежности с помощью драйвера JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Одна из сторон разработки приложений, характерная для всех приложений — постоянная необходимость улучшения производительности и надежности. Существует несколько способов достижения этих целей с помощью драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
В подразделах данного раздела приводится описание различных способов улучшения производительности и надежности приложения при использовании драйвера JDBC.  

## <a name="in-this-section"></a>в этом разделе

|Раздел|Описание|  
|-----------|-----------------|  
|[Закрытие неиспользуемых объектов](../../connect/jdbc/closing-objects-when-not-in-use.md)|Описывается важность закрытия объектов драйвера JDBC, когда в них больше нет необходимости.|  
|[Управление размером транзакции](../../connect/jdbc/managing-transaction-size.md)|Описываются способы улучшения производительности транзакций.|  
|[Работа с инструкциями и результирующими наборами](../../connect/jdbc/working-with-statements-and-result-sets.md)|Описываются способы улучшения производительности при работе с объектами инструкции или результирующий набор.|  
|[Использование адаптивной буферизации](../../connect/jdbc/using-adaptive-buffering.md)|Описывается функция адаптивной буферизации, разработанная для получения любых данных большого объема и позволяющая избежать излишней нагрузки, связанной с использованием серверных курсоров.|  
|[Разреженные столбцы](../../connect/jdbc/sparse-columns.md)|Описывает поддержку разреженных столбцов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в драйвере JDBC.|  
|[Кэширование метаданных подготовленной инструкции для JDBC Driver](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Описывает способы улучшения производительности с запросами подготовленной инструкции.|
|[Использование API массового копирования для операции пакетной вставки](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|В этой статье описывается включение интерфейс API массового копирования для операций вставки и ее преимущества.|

## <a name="see-also"></a>См. также раздел

[Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
