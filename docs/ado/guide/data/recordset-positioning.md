---
title: Позиционирование в наборе записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f37f69b64e4a1a7fd55fb24a0c85d515971d4e72
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910454"
---
# <a name="recordset-positioning"></a>Позиционирование в наборе записей
Используйте **примеры AbsolutePosition** значение, чтобы перейти к записи в зависимости от его порядковый номер в **записей** объекта, или чтобы определить порядковый номер текущей записи. Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступен.  
  
 **Примеры AbsolutePosition** отсчитывается от 1, и равняется 1 при первой записи в текущей записи **записей**. Как упоминалось ранее, можно получить общее число записей в **записей** объекта из **RecordCount** свойство.  
  
 При задании **примеры AbsolutePosition** свойство, даже если это запись в текущем кэше ADO перезагружает кэша с новой группой записей, начиная с записи, вы указали. **CacheSize** свойство определяет размер этой группы.  
  
> [!NOTE]
>  Не следует использовать **примеры AbsolutePosition** свойство как число записей суррогат. Определенной записи перемещается при удалении предыдущей записи. Нет также никакой гарантий, что определенной записи будет иметь тот же **примеры AbsolutePosition** Если **записей** опросить или повторном открытии объекта. Закладки являются рекомендуемым способом сохранения и возврат к заданной позиции и являются единственным способом размещения во всех типах **записей** объектов.
