---
title: Команды для базового поставщика данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 231d9ced5bf370b8ee7c507e930e6961cfbed5a8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700577"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Выдача команды для базового поставщика данных
Любую команду, которая не начинается с ФИГУРОЙ передается через поставщик данных. Это эквивалентно при выполнении команды фигуры в форме «SHAPE {команды поставщика}». Эти команды выполняют *не* создать **записей**. Например «ФИГУРЫ {DROP ТАБЛИЦУ MyTable} — это допустимые фигуры команда, при условии, что поставщик данных поддерживает DROP TABLE.  
  
 Эта возможность позволяет обычного поставщика команд и команд формы для совместного использования одного соединения и транзакции.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формального формирования данных](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
