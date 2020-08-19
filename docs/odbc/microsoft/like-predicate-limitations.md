---
description: Ограничения предиката LIKE
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
ms.openlocfilehash: 63410b78b6d0b7ab59dd74b9f69fe57fe498c6ea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483527"
---
# <a name="like-predicate-limitations"></a>Ограничения предиката LIKE
Если длина данных в столбце превышает 255 символов, сравнение LIKE будет основано только на первых 255 символах.  
  
 , Как используется в процедуре, поддерживается только с шаблонами констант. Драйверы базы данных для настольных систем поддерживают SQL-92, например сопоставление шаблонов.  
  
 Использование предложения ESCAPE в предикате LIKE не поддерживается.  
  
 Сравнение со значением LIKE не должно выполняться для столбца, содержащего данные типа данных numeric или float. Результаты могут быть непредсказуемыми. Дополнительные сведения см. в *статье Microsoft Jet ядро СУБД программиста*.
