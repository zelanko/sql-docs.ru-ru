---
title: "Пользовательские свойства ADO NET | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2823f22fa0396451fbf5de1b5dd3840559ca1e02
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="ado-net-custom-properties"></a>Пользовательские свойства ADO NET
  **Пользовательские свойства источника**  
  
 Источник «ADO NET» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства источника «ADO NET». Все свойства доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Description|  
|-------------------|---------------|-----------------|  
|CommandTimeout|String|Задает число секунд до истечения времени ожидания команды SQL. Значение 0 означает, что время выполнения команды не ограничено.|  
|SqlCommand|String|Инструкция SQL, используемая источником «ADO NET» для извлечения данных.<br /><br /> При загрузке пакета можно динамически обновлять это свойство инструкцией SQL, которая будет использована источником «ADO NET». Дополнительные сведения см. в разделах [Выражения служб Integration Services (SSIS)](../../integration-services/expressions/integration-services-ssis-expressions.md) и [Использование выражений свойств в пакетах](../../integration-services/expressions/use-property-expressions-in-packages.md).|  
|AllowImplicitStringConversion|Логическое значение|Значение, указывающее, происходят ли следующие события.<br /><br /> — Отмена формирования ошибки проверки в случае несоответствия типов внешних метаданных и типов выходных столбцов, являющихся строковыми (DT_WSTR или DT_NTEXT).<br /><br /> — Неявное преобразование типов внешних метаданных к строковому типу данных, используемому в выходном столбце.<br /><br /> <br /><br /> Значение по умолчанию — TRUE.<br /><br /> Дополнительные сведения см. в статье [ADO NET Source](../../integration-services/data-flow/ado-net-source.md).|  
  
 Выход и выходные столбцы источника «ADO NET» не имеют пользовательских свойств.  
  
 Дополнительные сведения см. в статье [ADO NET Source](../../integration-services/data-flow/ado-net-source.md).  
  
 **Пользовательские свойства назначений**  
  
 Назначение [!INCLUDE[vstecado](../../includes/vstecado-md.md)] обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения « [!INCLUDE[vstecado](../../includes/vstecado-md.md)] ». Все свойства доступны для чтения и записи. Эти свойства недоступны в диалоговом окне **Редактор назначения «ADO.NET»**, однако их можно установить при помощи окна **Расширенный редактор**.  
  
|Свойство|Тип данных|Description|  
|--------------|---------------|-----------------|  
|BatchSize|Целочисленный|Количество строк в пакете, отправленном серверу. Значение **0** означает, что размер пакета соответствует размеру внутреннего буфера. Значение этого свойства по умолчанию равно **0**.|  
|CommandTimeOut|Целочисленный|Максимальное время ожидания в секундах, в течение которого может выполняться команда SQL. Значение **0** указывает на бесконечное время работы. Значение этого свойства по умолчанию равно **0**.|  
|TableOrViewName|String|Имя целевой таблицы или представления.|  
  
 Дополнительные сведения см. в статье [ADO NET Destination](../../integration-services/data-flow/ado-net-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
