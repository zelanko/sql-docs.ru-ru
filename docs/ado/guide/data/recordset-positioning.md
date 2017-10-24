---
title: "Позиционирование записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aee0d64d0fe1e310f42d79de36f5cf36c3813bf3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-positioning"></a>Позиционирование записей
Используйте **AbsolutePosition** на основе свойства, чтобы перейти к записи по его порядковому номеру в **записей** объекта, или чтобы определить порядковый номер текущей записи. Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступно.  
  
 **AbsolutePosition** начинается с 1 и имеет значение 1, если текущая запись является первой записью в **записей**. Как упоминалось ранее, вы можете получить общее число записей в **записей** объекта из **RecordCount** свойство.  
  
 При задании **AbsolutePosition** свойство, даже если это записи в текущий кэш ADO перезагружает кэша с новой группой записей, начиная с указанной записи. **CacheSize** свойство определяет размер этой группы.  
  
> [!NOTE]
>  Не следует использовать **AbsolutePosition** свойство в качестве символов-заместителей номер записи. Позиция изменения определенной записи, при удалении предыдущей записи. Нет никакой гарантии, что данная запись будет иметь такой же также **AbsolutePosition** Если **записей** опросить или повторном открытии объекта. Закладки являются рекомендуемый способ сохранения и возврат к заданной позиции, а единственный способ размещения различных типов **записей** объектов.

