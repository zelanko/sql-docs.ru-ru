---
title: "Импорт данных из таблиц (Master Data Services) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5b83b1-8e40-4ef8-9ba8-4ea17a58b672
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 47c83a225b97e203875f940a03fe52db80525060
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="import-data-from-tables-master-data-services"></a>Импорт данных из таблиц (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]поддерживает массовое добавление данных в модель и их изменение.  
  
 **Предварительные требования**  
  
-   Необходимо иметь разрешение на вставку данных в stg.\<name > _Leaf, stg.\<name > _Consolidated, stg.\<имя > _relationship в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базы данных.  
  
-   Необходимо иметь разрешения на выполнение любой stg.udp_\<name > _Leaf, stg.udp\_\<имя > _Consolidated, или stg.udp\_\<имя > _Relationship хранимой процедуры в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базы данных.  
  
-   Эта модель не должна иметь состояние **Зафиксирована**.  
  
 **Добавление, обновление и удаление данных в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]**  
  
1.  Подготовьте элементы к импорту в соответствующую промежуточную таблицу в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , в том числе укажите значения обязательных полей. Общие сведения о промежуточных таблицах см. в разделе [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md).  
  
    -   Для конечных элементов таблицы — stg.\<name > _Leaf, где \<имя > ссылается на соответствующей сущности. Сведения о требуемых полях см. в разделе [Конечный элемент таблицы элементов (службы Master Data Services)](../master-data-services/leaf-member-staging-table-master-data-services.md).  
  
    -   Для консолидированных элементов таблицы — stg.\<name > _Consolidated. Сведения о требуемых полях см. в разделе [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Для перемещения расположения элементов в явных иерархиях, таблица — stg.\<name > _Relationship. Сведения о требуемых полях см. в разделе [Промежуточная таблица связей (службы Master Data Services)](../master-data-services/relationship-staging-table-master-data-services.md).  
  
         Общие сведения о перемещении элементов в явных иерархиях см. в разделе [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md).  
  
    -   Используя значение поля **ImportType** , укажите нужное действие: создание, деактивация или удаление элементов. Дополнительные сведения о значениях см. в разделах [Конечный элемент таблицы элементов (службы Master Data Services)](../master-data-services/leaf-member-staging-table-master-data-services.md) и [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Общие сведения о деактивации и удалении элементов см. в разделе [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md).  
  
2.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру ядра базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server Management Studio](http://msdn.microsoft.com/library/66a6b7b1-de6a-4161-82bd-98ded486947b).  
  
3.  Импортируйте данные в промежуточные таблицы с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server Import and Export Wizard](~/integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
4.  Загрузите данные из промежуточных таблиц в таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , выполнив одно из следующих действий:  
  
    -   Запустите промежуточную хранимую процедуру, которая соответствует промежуточной таблице, в которую нужно переместить данные.  
  
         Общие сведения о промежуточных хранимых процедурах и промежуточных таблицах см. в разделе [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md). Дополнительные сведения о параметрах для промежуточных хранимых процедур и пример кода см. в разделе [Промежуточная хранимая процедура (службы Master Data Services)](../master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Используйте функциональную область **Управление интеграцией** системы управления основными данными.  
  
         На странице **Промежуточные пакеты** в раскрывающемся списке выберите модель, к которой вы добавляете данные, и нажмите кнопку **Запустить пакеты**. Состояние пакетной обработки указывается в поле **Состояние** . Дополнительные сведения о состояниях см. в разделе [Состояния операции импорта (службы Master Data Services)](../master-data-services/import-statuses-master-data-services.md).  
  
         ![Промежуточные пакеты страницу в диспетчере основных данных](../master-data-services/media/mds-stagingbatchespage.png "промежуточного хранения пакетов страниц в диспетчере основных данных")  
  
         Промежуточный процесс запускается через промежутки времени, указанные с помощью параметра **Интервал промежуточных пакетов** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
5.  Просмотрите ошибки, возникшие во время помещения на промежуточное хранение и обработку. Дополнительные сведения см. в разделах [Просмотр ошибок, возникающих во время помещения на промежуточное хранение (службы Master Data Services)](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md) и [Ошибки промежуточного процесса (службы Master Data Services)](../master-data-services/staging-process-errors-master-data-services.md).  
  
6.  Проверьте данные с помощью бизнес-правил.  
  
     В диспетчере основных данных перейдите к функциональной области **Обозреватель** и примените бизнес-правила для проверки данных. Дополнительные сведения см. в разделе [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md). Для проверки данных также можно использовать хранимую процедуру. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
     При загрузке из промежуточных таблиц данные не проверяются автоматически с помощью бизнес-правил. Дополнительные сведения о том, что такое проверка и когда она выполняется, см. в разделе [Проверка (службы Master Data Services)](../master-data-services/validation-master-data-services.md).  
  
  

