---
title: XML для соответствия аналитики (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad9117eaaed992d692e5dd7686b6cc6463a2c8e5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="xml-for-analysis-compliance-xmla"></a>Соответствие спецификациям XML для аналитики (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Спецификации XML для аналитики 1.1 описывают открытый стандарт, поддерживающий доступ к данным в источнике данных, находящемся в Интернете. В этом разделе подробно описывается уровень совместимости со спецификацией XML для аналитики 1.1, поддерживаемый [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
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
|Команды XML для аналитики (XMLA), поддерживаемые методом Discover|Следующие команды поддерживаются спецификацией XML для аналитики 1.1:<br /><br /> [Элемент Statement &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживаются следующие команды:<br /><br /> [Элемент ALTER &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Резервное копирование элемента &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Элемент Batch &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Элемент BeginTransaction &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Элемент Cancel &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Элемент ClearCache &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Элемент CommitTransaction &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Создать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Удалить элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Элемент DesignAggregations &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Элемент DROP &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Элемент INSERT &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Заблокировать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Элемент MergePartitions &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Элемент NotifyTableChange &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Обработать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Элемент RESTORE &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Элемент RollbackTransaction &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Элемент Statement &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Элемент Subscribe &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Синхронизировать элемент & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Разблокировать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Элемент Update &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Элемент UpdateCells &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Ошибки столбцов в табличных наборах строк|Не приводятся в спецификации XML для аналитики 1.1.|[Ошибка](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) используется [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] отчетов об ошибках для элементов столбцов, содержащихся в [строки](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) элемента.|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики & #40; XML для Аналитики & #41; Ссылка](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
