---
title: "XML для соответствия аналитики (XMLA) | Документы Microsoft"
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
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9e4bab75508cf50144c7f200327e51d7e72cd756
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="xml-for-analysis-compliance-xmla"></a>Соответствие спецификациям XML для аналитики (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Спецификации XML для аналитики 1.1 описывающая открытый стандарт, поддерживающий доступ к источникам данных, которые находятся в Интернете. В этом разделе подробно описывается уровень совместимости со спецификацией XML для аналитики 1.1, поддерживаемый [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="compliant-items"></a>Элементы соответствия  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] соответствуют всем обязательным пунктам, перечисленным в спецификации XML для аналитики 1.1. Кроме того, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] реализуют следующий необязательный пункт, приведенный в спецификации XML для аналитики 1.1.  
  
|Элемент|Спецификация|Реализация|  
|----------|-------------------|--------------------|  
|Session support|Элементы заголовка SOAP, перечисленные в разделе «Support for Statefulness in XML for Analysis» спецификации XML для аналитики 1.1.|Все перечисленные элементы заголовка SOAP поддерживаются службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], как указано в спецификации.|  
  
## <a name="extensions"></a>Модули  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также расширяют спецификацию XML для аналитики 1.1 с целью поддержки следующих дополнительных функций и возможностей.  
  
|Элемент|Спецификация|Реализация|  
|----------|-------------------|--------------------|  
|Согласование протокола|В спецификации XML для аналитики 1.1 не содержится никаких сведений|Элемент ProtocolCapabilities заголовка, добавленные [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для поддержки согласования возможностей протокола.|  
|Команды XML для аналитики (XMLA), поддерживаемые методом Discover|Следующие команды поддерживаются спецификацией XML для аналитики 1.1:<br /><br /> [Элемент оператора &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживаются следующие команды:<br /><br /> [Изменить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Резервный элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Элемент Batch &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Элемент BeginTransaction &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Отменить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Элемент ClearCache &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Элемент CommitTransaction &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Создать элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Удалить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Элемент DesignAggregations &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Удалить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Вставить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Элемент lock &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Элемент MergePartitions &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Элемент NotifyTableChange &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Элемент Process &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Восстановить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Элемент RollbackTransaction &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Элемент оператора &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Подписка элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Синхронизировать элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Разблокировать элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Обновить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Элемент UpdateCells &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Ошибки столбцов в табличных наборах строк|Не приводятся в спецификации XML для аналитики 1.1.|[Ошибка](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) используется [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] отчетов об ошибках для элементов столбцов, содержащихся в [строки](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) элемента.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по XML для аналитики (XMLA)](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
