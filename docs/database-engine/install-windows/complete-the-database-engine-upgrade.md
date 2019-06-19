---
title: Завершение обновления ядра СУБД | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.prod: sql
ms.technology: install
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 4fe57da44076bd33c585d4ab9986cf373e311f8e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794988"
---
# <a name="complete-the-database-engine-upgrade"></a>Завершение обновления ядра СУБД

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

После завершения обновления SQL Server вам, возможно, потребуется выполнить некоторые дополнительные действия. следующие основные параметры.  
  
После обновления компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]выполните следующие действия.  
  
- **Резервное копирование баз данных**. Создание полной резервной копии каждой базы данных.  

- **Используйте новые возможности**. Некоторые изменения SQL Server 2016 и SQL Server 2017 становятся доступны только после изменения уровня совместимости базы данных DATABASE_COMPATIBILITY до 130 или выше.  Дополнительные сведения и рекомендуемый рабочий процесс см. в разделе [Изменение режима совместимости базы данных и использование хранилища запросов](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md). Если база данных содержит оптимизированные для памяти таблицы, созданные в SQL Server 2014, см. статью [Статистика для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/statistics-for-memory-optimized-tables.md).
  
- **Службы Integration Services.**  
  
     Миграция пакетов служб Integration Services в формат [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Дополнительные сведения см. в разделе [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
- **Службы Reporting Services:** в случае обновления методом новой установки восстановите ключи шифрования служб Reporting Services. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
- **Master Data Services:**  обновите схему базы данных MDS и создайте веб-приложение SQL Server 2017. Дополнительные сведения см. в статье [Обновление служб Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md).  
  
- **Data Quality Services:** обновите схему базы данных DQS и проверьте обновление этой схемы. Дополнительные сведения см. в статье [Обновление служб Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
  
- **Полнотекстовый поиск**. Для обеспечения семантической согласованности результатов запроса заполните полнотекстовые каталоги повторно. Дополнительные сведения см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
