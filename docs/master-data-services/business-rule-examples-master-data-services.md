---
title: Примеры бизнес-правил
ms.custom: ''
ms.date: 01/05/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3974b9be-4b7c-4a37-ab26-1a36ef455744
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 79cf6243b275ba6090eb76400a8dbf7f8dd01f0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728701"
---
# <a name="business-rule-examples-master-data-services"></a>Примеры бизнес-правил (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье приводятся примеры бизнес-правил для [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. Эти примеры можно найти в образцах моделей, которые устанавливаются вместе с [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].   
  
Инструкции по развертыванию образцов моделей см. в разделе [Установка и настройка служб Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md).  
  
  
## <a name="business-rule-examples"></a>Примеры бизнес-правил  
Образец модели |Сущность  |Имя бизнес-правила| Description  
---------|---------|---------|-----------|  
Клиент    | Клиент   | Персональные условия оплаты| Задает условия оплаты по умолчанию для заказчиков.          
В следующем бизнес-правиле, если значение атрибута CustomerType соответствует `is equal` [](../master-data-services/business-rule-conditions-master-data-services.md), то `defaults to` [](../master-data-services/business-rule-conditions-master-data-services.md) применяется к атрибуту PaymentTerms. В противном случае не выполняется никаких действий.  
```  
If  
    CustomerType is equal to 2  
Then  
    PaymentTerms defaults to CASH  
Else  
    None      
```  
  
**--------------------------------------------------**  
  
Образец модели  |Сущность  |Имя бизнес-правила|Description    
---------|---------|---------|---------------  
Клиент     | Клиент    | Условия оплаты для организаций | Определяет условия оплаты по умолчанию для организаций.         
В следующем бизнес-правиле, если значение атрибута CustomerType соответствует `is equal` [](../master-data-services/business-rule-conditions-master-data-services.md), то `defaults to` [](../master-data-services/business-rule-actions-master-data-services.md) применяется к атрибуту PaymentTerms. В противном случае не выполняется никаких действий.  
```  
If  
    CustomerType is equal to 1  
Then  
    PaymentTerms defaults to 210Net30  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Образец модели  |Сущность  |Имя бизнес-правила| Description    
---------|---------|---------|-----------  
Продукт     |  Продукт       | DaysToManufacture |Задает диапазон сроков собственного производства.          
В следующем бизнес-правиле, если значение атрибута InHouseManufacture соответствует `is equal` [](../master-data-services/business-rule-conditions-master-data-services.md), то `must be between` [](../master-data-services/business-rule-actions-master-data-services.md) применяется к атрибуту DaysToManufacture. В противном случае не выполняется никаких действий.  
```  
If  
    InHouseManufacture is equal to Y  
Then  
    DaysToManufacture must be between 1 and 10  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Образец модели  |Сущность  |Имя бизнес-правила|Description    
---------|---------|---------|-------------  
Продукт     |Продукт         |Обязательные поля| Задает обязательные поля для элементов сущности продукта.           
В следующем правиле `is required` [](../master-data-services/business-rule-actions-master-data-services.md) выполняется для указанных атрибутов при любых условиях. Значения атрибутов не могут быть Null или пустыми.  
```  
If  
    None  
Then  
    Name is required  
    ProductSubCategory is required  
    Color is required  
    StandardCost is required  
    SafetyStockLevel is required  
    ReorderPoint is required  
    InHouseManufacture is required  
    SellStartDate is required  
    FinishedGoodIndicator is required  
    ProductLine is required  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Образец модели  |Сущность  |Имя бизнес-правила|Description    
---------|---------|---------|-----------  
Продукт     | Продукт        |  Стандартная стоимость| Устанавливает требование, согласно которому стандартная стоимость должна быть больше 0.        
В следующем бизнес-правиле `must be greater than` [](../master-data-services/business-rule-actions-master-data-services.md) применяется к атрибуту StandardCost продуктов при любых условиях.  
```  
If  
    None  
Then  
    StandardCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Образец модели  |Сущность  |Имя бизнес-правила|Description    
---------|---------|---------|------------  
Продукт     | Продукт        | Стоимость MSRP FG|Указывает, что для готовой продукции розничная цена производителя и цена продавца должны быть больше 0.           
  
В следующем бизнес-правиле, если значение атрибута FinishedGoodIndicator соответствует `is equal` [](../master-data-services/business-rule-conditions-master-data-services.md), то `must be greater than` [](../master-data-services/business-rule-actions-master-data-services.md) применяется к атрибутам MSRP и DealerCost.  
```  
If  
    FinishedGoodIndicator is equal to Y  
Then  
    MSRP must be greater than 0  
    DealerCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Образец модели  |Сущность  |Имя бизнес-правила|Description    
---------|---------|---------|------------  
Продукт     | Продукт        |  Имя по умолчанию| Задает название продукта по умолчанию на основе значений атрибутов Color и Class. Если значение атрибута Color не равно YLO, а значение атрибута Class не равно NA, название по умолчанию — Yellow NA.         
В следующем бизнес-правиле, если значения атрибутов Color и Class не соответствуют условию правила `is equal` , то `defaults to` [](../master-data-services/business-rule-actions-master-data-services.md) применяется к атрибуту Name.  
```  
If  
    (Color is equal to YLO AND Class is equal to NA) is not true  
Then  
    Name defaults to Yellow NA  
Else  
    Name defaults to Other  
```  
  
**--------------------------------------------------**  
  
  
**Просмотр примеров бизнес-правил в образцах моделей**  
1. Перейдите на веб-сайт [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] , настроенный после установки служб MDS, и щелкните поле **Администрирование системы** .   
Инструкции по настройке веб-сайта см. в разделе [Установка и настройка служб Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md).  
2. Щелкните образец модели, содержащий бизнес-правило из приведенных выше таблиц, а затем щелкните **Сущности**.  
3. Выберите сущность, к которой применяется правило, как указано в таблицах выше, а затем щелкните **Бизнес-правила**.  
4. Щелкните имя бизнес-правила, которое нужно просмотреть. В пользовательском интерфейсе отобразятся инструкции **If**, **Then** и **Else**.  
  
 
  
  
  
  

