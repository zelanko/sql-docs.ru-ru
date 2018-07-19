---
title: XML для аналитики (XMLA) соответствия | Документация Майкрософт
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b618fdd8cca3faed72afb0276f18cd928a3f31f7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051592"
---
# <a name="xml-for-analysis-xmla-compliance"></a>XML для аналитики (XMLA) соответствия
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]  

  Спецификации XML для аналитики 1.1 описывают открытый стандарт, поддерживающий доступ к данным в источнике данных, находящемся в Интернете. В этом разделе подробно описывается уровень соответствия спецификации XML для аналитики 1.1, поддерживаемый Azure Analysis Services и SQL Server Analysis Services.  
  
## <a name="compliant-items"></a>Элементы соответствия  
Службы Analysis Services соответствует всем обязательным пунктам, перечисленным в спецификации XML для аналитики 1.1. Кроме того службы Analysis Services реализует следующий необязательный пункт, описанной в спецификации XML для аналитики 1.1.  
  
|Элемент|Спецификация|Реализация|  
|----------|-------------------|--------------------|  
|Session support|Элементы заголовка SOAP, перечисленные в разделе «Support for Statefulness in XML for Analysis» спецификации XML для аналитики 1.1.|Все перечисленные элементы заголовка SOAP поддерживаются службами Analysis Services, как описано в спецификации.|  
  
## <a name="extensions"></a>Модули  
 Службы Analysis Services также расширяет спецификации XML для аналитики 1.1 для поддержки следующих дополнительных функций и возможностей.  
  
|Элемент|Спецификация|Реализация|  
|----------|-------------------|--------------------|  
|Согласование протокола|В спецификации XML для аналитики 1.1 не содержится никаких сведений|Элемент ProtocolCapabilities заголовка, добавить службами Analysis Services для поддержки согласования возможностей протокола.|  
|Команды XML для аналитики (XMLA), поддерживаемые методом Discover|Следующие команды поддерживаются спецификацией XML для аналитики 1.1:<br /><br /> [Элемент оператора &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Следующие команды поддерживаются службами Analysis Services:<br /><br /> [Элемент ALTER &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Резервное копирование элемента &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Элемент Batch &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Элемент BeginTransaction &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Элемент Cancel &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Элемент ClearCache &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Элемент CommitTransaction &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Создать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Удалить элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Элемент DesignAggregations &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Элемент DROP &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Вставка элемента &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Заблокировать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Элемент MergePartitions &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Элемент NotifyTableChange &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Обработать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Элемент RESTORE &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Элемент RollbackTransaction &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Элемент оператора &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Элемент Subscribe &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Элемент Synchronize &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Разблокировать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Элемент Update &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Элемент UpdateCells &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Ошибки столбцов в табличных наборах строк|Не приводятся в спецификации XML для аналитики 1.1.|[Ошибка](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) используются службами Analysis Services для сообщения об ошибках для элементов столбцов, содержащихся в [строки](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) элемент.|  
  
## <a name="see-also"></a>См. также
 [Справочник по XML для аналитики (XMLA)](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
