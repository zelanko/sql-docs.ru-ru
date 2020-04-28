---
title: Ограничения предиката LIKE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d596d688956d7bdbf3d9125184d81c16249781c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298964"
---
# <a name="like-predicate-limitations"></a>Ограничения предиката LIKE
Если длина данных в столбце превышает 255 символов, сравнение LIKE будет основано только на первых 255 символах.  
  
 , Как используется в процедуре, поддерживается только с шаблонами констант. Драйверы базы данных для настольных систем поддерживают SQL-92, например сопоставление шаблонов.  
  
 Использование предложения ESCAPE в предикате LIKE не поддерживается.  
  
 Сравнение со значением LIKE не должно выполняться для столбца, содержащего данные типа данных numeric или float. Результаты могут быть непредсказуемыми. Дополнительные сведения см. в *статье Microsoft Jet ядро СУБД программиста*.
