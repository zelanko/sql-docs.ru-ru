---
title: Стандартный синтаксический анализ | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- standard parse [Integration Services]
- locales [Integration Services]
ms.assetid: dfe835b1-ea52-4e18-a23a-5188c5b6f013
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2a6d0b88805c1e6fb86e7656d96cc0be7fa045f8
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389213"
---
# <a name="standard-parse"></a>Standard Parse
  Стандартный синтаксический анализ является зависящим от локалей набором процедур синтаксического анализа, которые поддерживают все преобразования типов данных, предоставляемые API-интерфейсами автоматизации преобразования типов данных, доступными в библиотеках Oleaut32.dll и Ole2dsip.dll. Стандартный синтаксический анализ является эквивалентом API-интерфейсов синтаксического анализа OLE DB.  
  
 Стандартный синтаксический анализ поддерживает преобразование международных типов данных, которое нужно использовать, если формат данных не поддерживается быстрым синтаксическим анализом. Дополнительные сведения об API-интерфейсе автоматизации преобразования типов данных см. в статье «API-интерфейсы преобразования типов данных» в [библиотеке MSDN](https://go.microsoft.com/fwlink/?LinkId=79427).  
  
## <a name="see-also"></a>См. также  
 [Быстрый синтаксический анализ](../../2014/integration-services/fast-parse.md)  
  
  
