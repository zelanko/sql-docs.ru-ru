---
title: Повышение надежности и производительности с помощью JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c71763fcd3d51138ac35cabd207cc39c268ceed
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028012"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Повышение производительности и надежности с помощью JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Одна из сторон разработки приложений, характерная для всех приложений — постоянная необходимость улучшения производительности и надежности. Существует несколько способов достижения этих целей с помощью драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
В подразделах данного раздела приводится описание различных способов улучшения производительности и надежности приложения при использовании драйвера JDBC.  

## <a name="in-this-section"></a>В этом разделе

|Раздел|Описание|  
|-----------|-----------------|  
|[Закрытие неиспользуемых объектов](../../connect/jdbc/closing-objects-when-not-in-use.md)|Описывается важность закрытия объектов драйвера JDBC, когда в них больше нет необходимости.|  
|[Управление размером транзакций](../../connect/jdbc/managing-transaction-size.md)|Описываются способы улучшения производительности транзакций.|  
|[Работа с инструкциями и результирующими наборами](../../connect/jdbc/working-with-statements-and-result-sets.md)|Описывает методы повышения производительности при использовании операторов или объектов ResultSet.|  
|[Использование адаптивной буферизации](../../connect/jdbc/using-adaptive-buffering.md)|Описывается функция адаптивной буферизации, разработанная для получения любых данных большого объема и позволяющая избежать излишней нагрузки, связанной с использованием серверных курсоров.|  
|[Разреженные столбцы](../../connect/jdbc/sparse-columns.md)|Описывает поддержку разреженных столбцов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в драйвере JDBC.|  
|[Кэширование метаданных подготовленной инструкции для JDBC Driver](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Описывает методы повышения производительности с помощью подготовленных запросов инструкций.|
|[Использование API массового копирования для операции пакетной вставки](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|Описывает, как включить API-интерфейс полного копирования для операций пакетной вставки и его преимуществ.|

## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
