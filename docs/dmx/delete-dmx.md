---
title: DELETE (DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DELETE
dev_langs:
- DMX
helpviewer_keywords:
- DELETE statement [DMX]
- mining structures [DMX], clearing
- clearing mining models
- deleting mining models
- mining models [Analysis Services], clearing
- deleting mining structures
ms.assetid: 5a8204c3-a3df-4d97-9c1d-d997d24c70e3
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 566ae835ad06e99edbf624ab6d25611c0a8427f7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="delete-dmx"></a>DELETE (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Позволяет удалить модель, структуру интеллектуального анализа данных или структуру вместе со всеми связанными моделями, в зависимости от используемых предложений расширений интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Аргументы  
 *model*  
 Идентификатор модели.  
  
 *Структура*  
 Идентификатор структуры.  
  
## <a name="remarks"></a>Remarks  
 Если вы не укажете **модель интеллектуального анализа данных** или **СТРУКТУРА интеллектуального анализа данных**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] выполняет поиск типа объекта, на основе имени и обрабатывает корректный объект. Если сервер содержит структуру и модель интеллектуального анализа данных с одинаковыми именами, возвращается ошибка.  
  
 В следующей таблице описан результат использования различных форм синтаксиса.  
  
|.|Результат|  
|---------------|------------|  
|УДАЛИТЬ из СТРУКТУРЫ интеллектуального анализа данных*\<структура >*<br /><br /> или диспетчер конфигурации служб<br /><br /> УДАЛИТЬ из СТРУКТУРЫ интеллектуального анализа данных*\<структуры >*. СОДЕРЖИМОЕ|Выполняет ProcessClear структуры интеллектуального анализа данных. Все содержимое структуры интеллектуального анализа данных и связанных с ней моделей интеллектуального анализа данных удаляется.|  
|УДАЛИТЬ из СТРУКТУРЫ интеллектуального анализа данных*\<структуры >*. ВАРИАНТЫ|Выполняет ProcessClearStructureOnly структуры интеллектуального анализа данных. Все содержимое структуры интеллектуального анализа данных удаляется, а связанные с ней модели интеллектуального анализа данных остаются без изменений. После удаления структуры интеллектуального анализа данных детализация связанных с ней моделей становится невозможной.|  
|УДАЛИТЬ из МОДЕЛИ интеллектуального анализа данных*\<модели >*<br /><br /> или диспетчер конфигурации служб<br /><br /> УДАЛИТЬ из МОДЕЛИ интеллектуального анализа данных*\<модели >*. СОДЕРЖИМОЕ|Выполняет ProcessClear по модели интеллектуального анализа данных, но значения состояний оставляются без изменений. Значения состояний представляют собой возможные состояния столбца. Например, значениями состояний для столбца «Пол» являются «Мужской» и «Женский».|  
  
 Дополнительные сведения о типах обработки см. в разделе [элемента типа &#40; XML для Аналитики &#41; ](../analysis-services/xmla/xml-elements-properties/type-element-xmla.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример удаляет все содержимое модели NB_Sample.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
