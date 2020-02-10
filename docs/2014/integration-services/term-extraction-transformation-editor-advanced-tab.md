---
title: Редактор преобразования "Извлечение терминов" (вкладка "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bc333bae08cd9ec658b6e8050b869d1232dbe629
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055273"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Редактор преобразования «Извлечение терминов» (вкладка «Дополнительно»)
  Вкладка **Дополнительно** диалогового окна **Редактор преобразования «Извлечение терминов»** используется для задания свойств извлечения, таких как частота, длина и предмет извлечения (слова или фразы).  
  
 Дополнительные сведения о преобразовании «Извлечения терминов» см. в разделе [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Сочетание**  
 Указывает, что при преобразовании будут извлекаться только отдельные существительные.  
  
 **Субстантивные словосочетания**  
 Указывает, что при преобразовании будут извлекаться только субстантивные словосочетания.  
  
 **Существительное и субстантивные словосочетание**  
 Указывает, что при преобразовании будут извлекаться как существительные, так и субстантивные словосочетания.  
  
 **Frequency**  
 Указывает, что целевой функцией является частота термина.  
  
 **TFIDF**  
 Указывает, что целевой функцией является значение TFIDF термина. Функция TFIDF расшифровывается как "частота термина и обратная частота документа" (Term Frequency and Inverse Document Frequency) и определяется формулой: TFIDF термина T = (частота_T) * log (#число_строк_во_входных_данных) / (#число_строк_включающих_T)  
  
 **Порог частоты**  
 Позволяет задать число вхождений слова или фразы, необходимое для их извлечения. Значение по умолчанию — 2.  
  
 **Максимальная длина термина**  
 Позволяет задать максимальную длину фразы или слова. Этот параметр затрагивает только субстантивные словосочетания. По умолчанию используется значение 12.  
  
 **Использовать Извлечение терминов с учетом регистра**  
 Указывает, будет ли учитываться регистр при извлечении. Значение по умолчанию — `False`.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) для указания метода обработки ошибок для строк, вызвавших ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Извлечение терминов" &#40;вкладка "Извлечение терминов"&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Редактор преобразования "Извлечение терминов" &#40;вкладка "исключения"&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [преобразование «Уточняющий запрос термина»](data-flow/transformations/lookup-transformation.md)  
  
  
