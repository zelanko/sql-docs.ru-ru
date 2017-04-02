---
title: "Примеры бизнес-правил (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "01/05/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3974b9be-4b7c-4a37-ab26-1a36ef455744
caps.latest.revision: 21
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 19
---
# Примеры бизнес-правил (службы Master Data Services)
В этой статье приводятся примеры бизнес-правил для [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. Эти примеры можно найти в образцах моделей, которые устанавливаются вместе с [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].   
  
Инструкции по развертыванию образцов моделей см. в разделе [Службы Master Data Services](../sql-server/media/master-data-services.png#deploySample).  
  
  
## Примеры бизнес-правил  
Образец модели |Сущность  |Имя бизнес-правила| Description  
---------|---------|---------|-----------|  
Customer    | Customer   | Персональные условия оплаты| Задает условия оплаты по умолчанию для заказчиков.          
В следующем бизнес-правиле, если значение атрибута CustomerType соответствует [условию правила](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, то [действие правила](../master-data-services/business-rule-conditions-master-data-services.md) `defaults to` применяется к атрибуту PaymentTerms. В противном случае не выполняется никаких действий.  
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
Customer     | Customer    | Условия оплаты для организаций | Определяет условия оплаты по умолчанию для организаций.         
В следующем бизнес-правиле, если значение атрибута CustomerType соответствует [условию правила](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, то [действие правила](../master-data-services/business-rule-actions-master-data-services.md) `defaults to` применяется к атрибуту PaymentTerms. В противном случае не выполняется никаких действий.  
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
В следующем бизнес-правиле, если значение атрибута InHouseManufacture соответствует [условию правила](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, то [действие правила](../master-data-services/business-rule-actions-master-data-services.md) `must be between` применяется к атрибуту DaysToManufacture. В противном случае не выполняется никаких действий.  
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
В следующем правиле [действие проверки](../master-data-services/business-rule-actions-master-data-services.md) `is required` выполняется для указанных атрибутов при любых условиях. Значения атрибутов не могут быть Null или пустыми.  
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
В следующем бизнес-правиле [действие правила](../master-data-services/business-rule-actions-master-data-services.md) `must be greater than` применяется к атрибуту StandardCost продуктов при любых условиях.  
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
  
В следующем бизнес-правиле, если значение атрибута FinishedGoodIndicator соответствует [условию правила](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, то [действие правила](../master-data-services/business-rule-actions-master-data-services.md) `must be greater than` применяется к атрибутам MSRP и DealerCost.  
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
Продукт     | Продукт        |  Имя по умолчанию| Задает название продукта по умолчанию на основе значений атрибутов Color и Class. Если значение атрибута Color не равно YLO, а значение атрибута Class не равно NA, название по умолчанию — Yellow NA.         
В следующем бизнес-правиле, если значения атрибутов Color и Class не соответствуют условию правила `is equal`, то [[действие правила](../master-data-services/business-rule-actions-master-data-services.md)](Business%20Rule%20Conditions%20(Master%20Data%20Services).xml) `defaults to` применяется к атрибуту Name.  
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
1. Перейдите на веб-сайт [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], настроенный после установки служб MDS, и щелкните поле **Администрирование системы**.   
Инструкции по настройке веб-сайта см. в разделе [Службы Master Data Services](../sql-server/media/master-data-services.png).  
2. Щелкните образец модели, содержащий бизнес-правило из приведенных выше таблиц, а затем щелкните **Сущности**.  
3. Выберите сущность, к которой применяется правило, как указано в таблицах выше, а затем щелкните **Бизнес-правила**.  
4. Щелкните имя бизнес-правила, которое нужно просмотреть. В пользовательском интерфейсе отобразятся инструкции **If**, **Then** и **Else**.  
  
## Эта статья помогла вам? Мы слушаем   
Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com).   
  
  
  
  
