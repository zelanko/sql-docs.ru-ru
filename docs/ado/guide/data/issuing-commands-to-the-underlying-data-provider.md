---
title: "Выдача команды для базового поставщика данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 24498f4d57627a1a7fb265a22703c0e9f8e581af
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Выдача команды для базового поставщика данных
Любые команды, не начинается с ФОРМОЙ передается поставщику данных. Это эквивалентно выполнению инструкции команды фигуры в форме «Формы {команды поставщика}». Эти команды имеют *не* нужно создать **записей**. Для экземпляра «{DROP ТАБЛИЦЕ MyTable} имеет ФОРМУ команде правильный фигуры, при условии, что поставщик данных поддерживает DROP TABLE.  
  
 Эта возможность позволяет команд обычного поставщика и команд формы для совместного использования одного соединения и транзакции.  
  
## <a name="see-also"></a>См. также:  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
