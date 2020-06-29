---
title: Дополнение строк (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428139"
---
# <a name="string-padding-ssis"></a>Дополнение строк (службы SSIS)
  Средство оценки выражений не проверяет, содержит ли строка начальные и конечные пробелы, и не приводит строки к одинаковой длине перед их сравнением. Если выражения требуют дополнения строк, можно использовать оператор + для сцепления значений столбцов и пустых строк. Дополнительные сведения см. в разделе [+ (Объединение) (выражение SSIS)](concatenate-ssis-expression.md).  
  
 С другой стороны, если надо удалить лишние пробелы, средство оценки выражений предоставляет функции LTRIM, RTRIM и TRIM, которые удаляют начальные либо конечные пробелы, либо и те и другие. Дополнительные сведения см. в разделах [LTRIM (выражение служб SSIS)](trim-ssis-expression.md), [RTRIM (выражение служб SSIS)](rtrim-ssis-expression.md) и [TRIM (выражение служб SSIS)](trim-ssis-expression.md).  
  
> [!NOTE]  
>  Функция LEN включает в счет начальные и завершающие пробелы.  
  
## <a name="related-content"></a>См. также  
 Техническая статья [Памятка выражений служб SSIS](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
)на сайте pragmaticworks.com  
  
  
