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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b82c2758dbc796ec29dd7304ee821a1a018af0a8
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920738"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Повышение производительности и надежности с помощью JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Одна из сторон разработки приложений, характерная для всех приложений — постоянная необходимость улучшения производительности и надежности. Существует несколько способов достижения этих целей с помощью драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
В подразделах данного раздела приводится описание различных способов улучшения производительности и надежности приложения при использовании драйвера JDBC.  

## <a name="in-this-section"></a>В этом разделе

|Раздел|Description|  
|-----------|-----------------|  
|[Закрытие неиспользуемых объектов](../../connect/jdbc/closing-objects-when-not-in-use.md)|Описывается важность закрытия объектов драйвера JDBC, когда в них больше нет необходимости.|  
|[Управление размером транзакций](../../connect/jdbc/managing-transaction-size.md)|Описываются способы улучшения производительности транзакций.|  
|[Работа с инструкциями и результирующими наборами](../../connect/jdbc/working-with-statements-and-result-sets.md)|Сведения о том, как улучшить производительность при использовании объектов Statement или ResultSet.|  
|[Использование адаптивной буферизации](../../connect/jdbc/using-adaptive-buffering.md)|Описывается функция адаптивной буферизации, разработанная для получения любых данных большого объема и позволяющая избежать излишней нагрузки, связанной с использованием серверных курсоров.|  
|[Разреженные столбцы](../../connect/jdbc/sparse-columns.md)|Описывает поддержку разреженных столбцов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в драйвере JDBC.|  
|[Кэширование метаданных подготовленной инструкции для JDBC Driver](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Сведения о том, как улучшить производительность очередей для подготовленных инструкций.|
|[Использование API массового копирования для операции пакетной вставки](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|Сведения о том, как включить API-интерфейс массового копирования для операций пакетной вставки и преимущества этого интерфейса.|

## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
