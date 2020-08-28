---
description: Выдача команды для базового поставщика данных
title: Выдача команд базовому поставщику данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: rothja
ms.author: jroth
ms.openlocfilehash: d4f1db51d54b69bf42fe185d30b78df57b89df39
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980435"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Выдача команды для базового поставщика данных
Любая команда, которая не начинается с SHAPE, передается поставщику данных. Это эквивалентно выдаче команды Shape в виде "SHAPE {поставщик команда}". Этим командам *не* требуется создавать **набор записей**. Например, форма {DROP TABLE MyTable} является абсолютно допустимой командой Shape, предполагая, что поставщик данных поддерживает инструкцию DROP TABLE.  
  
 Эта возможность позволяет использовать как обычные команды поставщика, так и команды Shape для совместного использования одного соединения и транзакции.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](./data-shaping-example.md)   
 [Грамматика формальной фигуры](./formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](./shape-commands-in-general.md)