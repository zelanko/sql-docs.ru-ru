---
title: Нечеткий уточняющий (вкладка «Дополнительно») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 65c7acaab54bbbaa18126e9c1d2ac032e96557da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110201"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>Редактор преобразования «Нечеткий уточняющий запрос» (вкладка «Дополнительно»)
  Вкладка **Дополнительно** диалогового окна **Редактор преобразования «Нечеткий уточняющий запрос»** позволяет задать параметры нечеткого поиска.  
  
 Дополнительные сведения о преобразовании «Нечеткий уточняющий запрос» см. в разделе [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Максимальное количество совпадений, которое следует выводить на каждый уточняющий запрос**  
 Указывает максимальное число совпадений, возвращаемое преобразованием для каждой входной строки. Значение по умолчанию — **1**.  
  
 **Порог подобия**  
 Задает порог подобия на уровне компонента при помощи данного ползунка. Чем ближе значение к 1, тем ближе к искомому должно быть значение строки уточняющего запроса. Увеличение порогового значения может увеличить скорость соответствия, так как при этом будет рассматриваться меньшее количество предполагаемых совпадений.  
  
 **Разделители токенов**  
 Определяет разделители, используемые преобразованием для разделения значений столбца.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Нечеткий уточняющий &#40;ссылаться вкладка «таблица»&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Нечеткий уточняющий &#40;вкладка «столбцы»&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  