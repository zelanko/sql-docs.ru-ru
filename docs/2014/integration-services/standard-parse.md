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
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4f2a34753e16e035b91d879e081c7baad8739b79
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371986"
---
# <a name="standard-parse"></a>Standard Parse
  Стандартный синтаксический анализ является зависящим от локалей набором процедур синтаксического анализа, которые поддерживают все преобразования типов данных, предоставляемые API-интерфейсами автоматизации преобразования типов данных, доступными в библиотеках Oleaut32.dll и Ole2dsip.dll. Стандартный синтаксический анализ является эквивалентом API-интерфейсов синтаксического анализа OLE DB.  
  
 Стандартный синтаксический анализ поддерживает преобразование международных типов данных, которое нужно использовать, если формат данных не поддерживается быстрым синтаксическим анализом. Дополнительные сведения об API-интерфейсе автоматизации преобразования типов данных см. в статье «API-интерфейсы преобразования типов данных» в [библиотеке MSDN](https://go.microsoft.com/fwlink/?LinkId=79427).  
  
## <a name="see-also"></a>См. также  
 [Быстрый синтаксический анализ](../../2014/integration-services/fast-parse.md)  
  
  
