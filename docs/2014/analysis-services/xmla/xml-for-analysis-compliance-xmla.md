---
title: XML на соответствие аналитики (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc7a8da77b72f25a68764636fbe15bc2d9e4ae04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267090"
---
# <a name="xml-for-analysis-compliance-xmla"></a>Соответствие спецификациям XML для аналитики (XMLA)
  Спецификации XML для аналитики 1.1 описывают открытый стандарт, поддерживающий доступ к данным в источнике данных, находящемся в Интернете. В этом разделе подробно описывается уровень соответствия спецификации XML для аналитики 1.1, поддерживаемый [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="compliant-items"></a>Элементы соответствия  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] соответствуют всем обязательным пунктам, перечисленным в спецификации XML для аналитики 1.1. Кроме того, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] реализуют следующий необязательный пункт, приведенный в спецификации XML для аналитики 1.1.  
  
|Элемент|Спецификация|Реализация|  
|----------|-------------------|--------------------|  
|Session support|Элементы заголовка SOAP, перечисленные в разделе «Support for Statefulness in XML for Analysis» спецификации XML для аналитики 1.1.|Все перечисленные элементы заголовка SOAP поддерживаются службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], как указано в спецификации.|  
  
## <a name="extensions"></a>Модули  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также расширяют спецификацию XML для аналитики 1.1 с целью поддержки следующих дополнительных функций и возможностей.  
  
|Элемент|Спецификация|Реализация|  
|----------|-------------------|--------------------|  
|Согласование протокола|В спецификации XML для аналитики 1.1 не содержится никаких сведений|[ProtocolCapabilities](xml-elements-headers/protocolcapabilities-element-xmla.md) элемент заголовка, добавленные [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для поддержки согласования возможностей протокола.|  
|Команды XML для аналитики (XMLA), поддерживаемые методом Discover|Следующие команды поддерживаются спецификацией XML для аналитики 1.1:<br /><br /> -   [Элемент оператора &#40;XML для Аналитики&#41;](xml-elements-commands/statement-element-xmla.md)|Службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживаются следующие команды:<br /><br /> -   [Элемент ALTER &#40;XML для Аналитики&#41;](xml-elements-commands/alter-element-xmla.md)<br />-   [Резервное копирование элемента &#40;XML для Аналитики&#41;](xml-elements-commands/backup-element-xmla.md)<br />-   [Элемент Batch &#40;XML для Аналитики&#41;](xml-elements-commands/batch-element-xmla.md)<br />-   [Элемент BeginTransaction &#40;XML для Аналитики&#41;](xml-elements-commands/begintransaction-element-xmla.md)<br />-   [Элемент Cancel &#40;XML для Аналитики&#41;](xml-elements-commands/cancel-element-xmla.md)<br />-   [Элемент ClearCache &#40;XML для Аналитики&#41;](xml-elements-commands/clearcache-element-xmla.md)<br />-   [Элемент CommitTransaction &#40;XML для Аналитики&#41;](xml-elements-commands/committransaction-element-xmla.md)<br />-   [Создать элемент &#40;XML для Аналитики&#41;](xml-elements-commands/create-element-xmla.md)<br />-   [Удалить элемент &#40;XML для Аналитики&#41;](xml-elements-commands/delete-element-xmla.md)<br />-   [Элемент DesignAggregations &#40;XML для Аналитики&#41;](xml-elements-commands/designaggregations-element-xmla.md)<br />-   [Элемент DROP &#40;XML для Аналитики&#41;](xml-elements-commands/drop-element-xmla.md)<br />-   [Вставка элемента &#40;XML для Аналитики&#41;](xml-elements-commands/insert-element-xmla.md)<br />-   [Заблокировать элемент &#40;XML для Аналитики&#41;](xml-elements-commands/lock-element-xmla.md)<br />-   [Элемент MergePartitions &#40;XML для Аналитики&#41;](xml-elements-commands/mergepartitions-element-xmla.md)<br />-   [Элемент NotifyTableChange &#40;XML для Аналитики&#41;](xml-elements-commands/notifytablechange-element-xmla.md)<br />-   [Обработать элемент &#40;XML для Аналитики&#41;](xml-elements-commands/process-element-xmla.md)<br />-   [Элемент RESTORE &#40;XML для Аналитики&#41;](xml-elements-commands/restore-element-xmla.md)<br />-   [Элемент RollbackTransaction &#40;XML для Аналитики&#41;](xml-elements-commands/rollbacktransaction-element-xmla.md)<br />-Элемент SetPasswordEncryptionKey<br />-   [Элемент оператора &#40;XML для Аналитики&#41;](xml-elements-commands/statement-element-xmla.md)<br />-   [Элемент Subscribe &#40;XML для Аналитики&#41;](xml-elements-commands/subscribe-element-xmla.md)<br />-   [Элемент Synchronize &#40;XML для Аналитики&#41;](xml-elements-commands/synchronize-element-xmla.md)<br />-   [Разблокировать элемент &#40;XML для Аналитики&#41;](xml-elements-commands/unlock-element-xmla.md)<br />-   [Элемент Update &#40;XML для Аналитики&#41;](xml-elements-commands/update-element-xmla.md)<br />-   [Элемент UpdateCells &#40;XML для Аналитики&#41;](xml-elements-commands/updatecells-element-xmla.md)|  
|Ошибки столбцов в табличных наборах строк|Не приводятся в спецификации XML для аналитики 1.1.|[Ошибка](xml-elements-properties/error-element-xmla.md) используется [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для сообщения об ошибках для элементов столбцов, содержащихся в [строки](xml-elements-properties/error-element-xmla.md) элемент.|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики &#40;XMLA&#41; ссылки](xml-for-analysis-xmla-reference.md)  
  
  
