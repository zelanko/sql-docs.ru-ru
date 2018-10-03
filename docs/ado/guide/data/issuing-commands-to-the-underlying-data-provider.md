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
manager: craigg
ms.openlocfilehash: 2267ff0af67682417b118e9fa01b2dceeb1454a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634752"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Выдача команды для базового поставщика данных
Любую команду, которая не начинается с ФИГУРОЙ передается через поставщик данных. Это эквивалентно при выполнении команды фигуры в форме «SHAPE {команды поставщика}». Эти команды выполняют *не* создать **записей**. Например «ФИГУРЫ {DROP ТАБЛИЦУ MyTable} — это допустимые фигуры команда, при условии, что поставщик данных поддерживает DROP TABLE.  
  
 Эта возможность позволяет обычного поставщика команд и команд формы для совместного использования одного соединения и транзакции.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формального формирования данных](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
