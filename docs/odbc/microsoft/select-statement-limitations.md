---
description: Ограничения инструкции SELECT
title: Ограничения инструкции SELECT | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 601c9a2fcd07d0c89003d9aa4d1b631e07ecbf90
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466416"
---
# <a name="select-statement-limitations"></a>Ограничения инструкции SELECT
Столбец агрегатной функции не может смешиваться со столбцом, не являющимся статистическим выражением, в инструкции SELECT.  
  
 Список выбора инструкции SELECT с предложением GROUP BY может содержать только выражения из предложения GROUP BY или функций Set.  
  
 Использование звездочки (для выбора всех столбцов) в инструкции SELECT, содержащей предложение GROUP BY, не поддерживается. Должны быть указаны имена столбцов, которые будут выбраны.  
  
 Использование вертикальной черты в инструкции SELECT не поддерживается. Используйте параметр в инструкции SELECT, если необходимо сослаться на значение данных, содержащее вертикальную черту.  
  
 При использовании псевдонима столбца в инструкции SELECT слово «AS» должно предшествовать псевдониму. Например, "выбрать col1 как a из b". Без "AS" инструкция возвратит ошибку.  
  
 Если в инструкции SELECT введено неправильное имя столбца, то вместо ошибки SQLSTATE S0022 (столбец не найден) возвращается ошибка SQLSTATE 07001, "неправильное количество параметров".  
  
 При использовании драйвера Microsoft Excel, если в столбец вставляется пустая строка, то пустая строка преобразуется в NULL. Поисковая инструкция SELECT, которая выполняется с пустой строкой в предложении WHERE, не будет выполнена для этого столбца.
