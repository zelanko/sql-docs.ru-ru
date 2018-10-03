---
title: Редактор преобразования извлечения терминов, в (вкладка «Дополнительно») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce44e2709013a6d56d47ad30c90ecf5d92825503
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185334"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Редактор преобразования «Извлечение терминов» (вкладка «Дополнительно»)
  Вкладка **Дополнительно** диалогового окна **Редактор преобразования «Извлечение терминов»** используется для задания свойств извлечения, таких как частота, длина и предмет извлечения (слова или фразы).  
  
 Дополнительные сведения о преобразовании «Извлечения терминов» см. в разделе [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Имя существительное**  
 Указывает, что при преобразовании будут извлекаться только отдельные существительные.  
  
 **Субстантивное словосочетание**  
 Указывает, что при преобразовании будут извлекаться только субстантивные словосочетания.  
  
 **Имя существительное и субстантивное словосочетание**  
 Указывает, что при преобразовании будут извлекаться как существительные, так и субстантивные словосочетания.  
  
 **Частота**  
 Указывает, что целевой функцией является частота термина.  
  
 **TFIDF**  
 Указывает, что целевой функцией является значение TFIDF термина. Функция TFIDF расшифровывается как "частота термина и обратная частота документа" (Term Frequency and Inverse Document Frequency) и определяется формулой: TFIDF термина T = (частота_T) * log (#число_строк_во_входных_данных) / (#число_строк_включающих_T)  
  
 **Порог частоты**  
 Позволяет задать число вхождений слова или фразы, необходимое для их извлечения. Значение по умолчанию — 2.  
  
 **Максимальная длина термина**  
 Позволяет задать максимальную длину фразы или слова. Этот параметр затрагивает только субстантивные словосочетания. Значение по умолчанию — 12.  
  
 **Учитывать регистр при извлечении терминов**  
 Указывает, будет ли учитываться регистр при извлечении. Значение по умолчанию — `False`.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) для указания метода обработки ошибок для строк, вызвавших ошибку.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования извлечения терминов &#40;вкладке извлечения терминов&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Редактор преобразования извлечения терминов &#40;вкладка "исключение"&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [Преобразование "Уточняющий запрос термина"](data-flow/transformations/lookup-transformation.md)  
  
  
