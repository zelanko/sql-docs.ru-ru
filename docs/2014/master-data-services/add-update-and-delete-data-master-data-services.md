---
title: Добавление, обновление и удаление данных (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a12c6dd3b0691d62f5509a363311b1deb1584078
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972304"
---
# <a name="add-update-and-delete-data-master-data-services"></a>Добавление, обновление и удаление данных (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]поддерживает массовое добавление данных в модель и их изменение.  
  
 **Предварительные требования**  
  
-   Необходимо иметь разрешение на вставку данных в STG. \<name> _Leaf STG. \<name> _Consolidated, stg. \<name> _Relationship таблицу в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базе данных.  
  
-   Необходимо иметь разрешения на выполнение хранимой процедуры STG. udp_ \<name> _Leaf, stg. udp \_ \<name> _Consolidated или stg. UDP \_ \<name> _Relationship в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базе данных.  
  
-   Эта модель не должна иметь состояние **Зафиксирована**.  
  
 **Добавление, обновление и удаление данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базе данных**  
  
1.  Подготовьте элементы к импорту в соответствующую промежуточную таблицу в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , в том числе укажите значения обязательных полей. Общие сведения о промежуточных таблицах см. в разделе [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   Для конечных элементов таблица является STG. \<name> _Leaf, где \<name> ссылается на соответствующую сущность. Сведения о требуемых полях см. в разделе [Конечный элемент таблицы элементов (службы Master Data Services)](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md).  
  
    -   Для консолидированных элементов таблица является STG. \<name> _Consolidated. Сведения о требуемых полях см. в разделе [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Для перемещения расположения элементов в явных иерархиях таблица является STG. \<name> _Relationship. Сведения о требуемых полях см. в разделе [Промежуточная таблица связей (службы Master Data Services)](../../2014/master-data-services/relationship-staging-table-master-data-services.md).  
  
         Общие сведения о перемещении элементов в явных иерархиях см. в разделе [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
    -   Используя значение поля **ImportType** , укажите нужное действие: создание, деактивация или удаление элементов. Дополнительные сведения о значениях см. в разделах [Конечный элемент таблицы элементов (службы Master Data Services)](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) и [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Общие сведения о деактивации и удалении элементов см. в разделе [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
2.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру ядра базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md).  
  
3.  Импортируйте данные в промежуточные таблицы с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server Import and Export Wizard](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
4.  Загрузите данные из промежуточных таблиц в таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , выполнив одно из следующих действий:  
  
    -   Запустите промежуточную хранимую процедуру, которая соответствует промежуточной таблице, в которую нужно переместить данные.  
  
         Общие сведения о промежуточных хранимых процедурах и промежуточных таблицах см. в разделе [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md). Дополнительные сведения о параметрах для промежуточных хранимых процедур и пример кода см. в разделе [Промежуточная хранимая процедура (службы Master Data Services)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Используйте функциональную область **Управление интеграцией** системы управления основными данными.  
  
         На странице **Промежуточные пакеты** в раскрывающемся списке выберите модель, к которой вы добавляете данные, и нажмите кнопку **Запустить пакеты**. Состояние пакетной обработки указывается в поле **Состояние** . Дополнительные сведения о состояниях см. в разделе [Состояния операции импорта (службы Master Data Services)](../../2014/master-data-services/import-statuses-master-data-services.md).  
  
         ![Страница промежуточных пакетов в диспетчере основных данных](../../2014/master-data-services/media/mds-staging-batches.png "Страница промежуточных пакетов в диспетчере основных данных")  
  
         Промежуточный процесс запускается через промежутки времени, указанные с помощью параметра **Интервал промежуточных пакетов** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md).  
  
5.  Просмотрите ошибки, возникшие во время помещения на промежуточное хранение и обработку. Дополнительные сведения см. [в разделе Просмотр ошибок, происходящих во время промежуточного процесса &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md) и [ошибки промежуточного процесса &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
6.  Проверьте данные с помощью бизнес-правил.  
  
     В диспетчере основных данных перейдите к функциональной области **Обозреватель** и примените бизнес-правила для проверки данных. Дополнительные сведения см. в разделе [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md). Для проверки данных также можно использовать хранимую процедуру. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
     При загрузке из промежуточных таблиц данные не проверяются автоматически с помощью бизнес-правил. Дополнительные сведения о том, что такое проверка и когда она выполняется, см. в разделе [Проверка (службы Master Data Services)](../../2014/master-data-services/validation-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Master Data Services &#40;импорта данных&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
