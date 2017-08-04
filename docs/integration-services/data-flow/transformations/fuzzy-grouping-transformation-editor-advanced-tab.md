---
title: "Нечеткое группирование преобразования, редактор (вкладка «Дополнительно») | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2eb40d25a2deef0cb95971bf73bb2af4d44cf3c2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a>Редактор преобразования «Нечеткое группирование» (вкладка «Дополнительно»)
  На вкладке **Дополнительно** диалогового окна **Редактор преобразования «Нечеткое группирование»** можно определить входные и выходные столбцы, пороги подобия и разделители токенов.  
  
> [!NOTE]  
>  Свойства **Exhaustive** и **MaxMemoryUsage** преобразования «Нечеткое группирование» недоступны в **Редакторе преобразования «Нечеткое группирование»**, однако они могут быть заданы при помощи **расширенного редактора**. Дополнительные сведения об этих свойствах см. в подразделе «Преобразование "Нечеткое группирование"» раздела [Transformation Custom Properties](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Дополнительные сведения о преобразовании «Нечеткое группирование» см. в разделе [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Имя входного ключевого столбца**  
 Укажите имя выходного столбца, содержащего уникальный идентификатор для каждой входной строки. Столбец **_key_in** содержит значение, уникально идентифицирующее каждую строку.  
  
 **Имя выходного ключевого столбца**  
 Укажите имя выходного столбца, содержащего уникальный идентификатор для канонической строки группы повторяющихся строк. Столбец **_key_out** соответствует значению **_key_in** канонической строки данных.  
  
 **Имя столбца порога подобия**  
 Укажите имя столбца, содержащего показатель подобия. Показатель подобия — значение от 0 до 1, представляющее собой степень подобия входной строки относительно канонической. Чем ближе к 1 коэффициент, тем более строка соответствует канонической.  
  
 **Порог подобия**  
 Установите порог подобия с помощью ползунка. Чем ближе порог к 1, тем большее сходство между собой должны иметь строки, считающиеся повторяющимися. Увеличение этого порога может повысить скорость нахождения совпадений, так как количество рассматриваемых потенциальных записей будет меньше.  
  
 **Разделители токенов**  
 В преобразовании имеется набор разделителей по умолчанию для разделения данных на лексемы. При необходимости можно добавить или удалить разделители в списке.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Определение подобных строк данных с помощью преобразования «Нечеткое группирование»](../../../integration-services/data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
