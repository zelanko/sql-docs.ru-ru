---
title: "Команды (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- commands [XML for Analysis]
- XML for Analysis, commands
- XMLA, commands
ms.assetid: c8a93ea6-8eb5-4204-b037-69cb442a0082
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c6a16dfc9dd0ff1c58edcc18c69c1d2f2709145a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="xml-elements---commands"></a>Элементы XML - команды
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]В этом разделе справки содержит XML для аналитики (XMLA) элементов, которые могут использоваться в **команда** во время выполнения **Execute** вызова метода.  
  
|Элемент|Description|  
|-------------|-----------------|  
|[Элемент Alter (XML для аналитики)](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)|Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) для изменения объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент BACKUP](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|Создает резервную копию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных в файл резервной копии.|  
|[Элемент Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)|Выполняет один или несколько XML для аналитики (XMLA) команды как пакетная операция последовательно или параллельно на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)|Начинает транзакцию в текущем сеансе с экземпляром служб Analysis Services.|  
|[Элемент Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|Отменяет команду, выполняющуюся в настоящий момент в экземпляре служб Analysis Services.|  
|[Элемент ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)|Очищает кэш памяти для указанного объекта в экземпляре служб Analysis Services.|  
|[Элемент CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)|Фиксирует транзакцию в текущем сеансе с экземпляром служб Analysis Services.|  
|[Создать элемент](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод для создания объектов в экземпляре служб Analysis Services.|  
|[Удаление элемента](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)|Удаляет объект в экземпляре служб Analysis Services.|  
|[Элемент DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)|Создает агрегаты для статистической схемы в экземпляре служб Analysis Services.|  
|[Элемент DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|Удаляет элементы атрибута из измерения.|  
|[Элемент INSERT](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)|Вставляет элементы атрибута в измерение.|  
|[Блокировать элемент](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)|Блокирует указанный объект в экземпляре служб Analysis Services.|  
|[Элемент MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)|Выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции.|  
|[Элемент NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)|Уведомляет экземпляр служб Analysis Services, что в таблицах указанного источника данных произошло изменение.|  
|[Элемент Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|Обрабатывает объекты в экземпляре служб Analysis Services.|  
|[Элемент RESTORE](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|Восстанавливает базу данных служб Analysis Services из файла резервной копии.|  
|[Элемент RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)|Выполняет откат транзакции в текущем сеансе с экземпляром служб Analysis Services.|  
|[Элемент Statement](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Содержит запрос или инструкцию, отправляемых с помощью [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метода с экземпляром служб Analysis Services.|  
|[Элемент Subscribe](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)|Подписывается на трассировку и возвращает набор строк, содержащий события трассировки для экземпляра служб Analysis Services.|  
|[Элемент Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|Синхронизирует базу данных служб Analysis Services с другой базой данных.|  
|[Разблокировать элемент](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|Снимает указанную блокировку на экземпляре служб Analysis Services.|  
|[Элемент Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|Обновляет элементы атрибута в измерении.|  
|[Элемент UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|Обновляет ячейки в кубе, доступном для записи.|  
  
  
