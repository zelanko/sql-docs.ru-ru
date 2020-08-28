---
description: Гибридные команды
title: Гибридные команды | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- hybrid commands [ADO]
- data shaping [ADO], hybrid commands
ms.assetid: e8ca40e8-459c-40e2-8dd3-3ec6d5ee7b51
author: rothja
ms.author: jroth
ms.openlocfilehash: ec23a74b26be84684965c8e81fffbfd827a9981a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980515"
---
# <a name="hybrid-commands"></a>Гибридные команды
Гибридные команды являются частично параметризованными командами. Пример:  
  
```  
SHAPE {select * from plants}   
   APPEND( {select * from customers where country = ?}   
           RELATE PlantCountry TO PARAMETER 0,   
             PlantRegion TO CustomerRegion )   
```  
  
 Поведение кэширования для гибридной команды аналогично поведению обычных параметризованных команд.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](./data-shaping-example.md)   
 [Грамматика формальной фигуры](./formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](./shape-commands-in-general.md)