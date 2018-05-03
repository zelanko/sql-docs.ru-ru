---
title: С помощью AddNew в интерпретации и пакетного режима | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e2c7f2cdd8a983572dc75a0a976e76289044f80
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>С помощью AddNew в интерпретации и пакетного режима
Поведение **AddNew** метод зависит от режима обновления для **записей** объекта и ли передать *списка полей* и *значения*аргументы.  
  
 В режиме немедленного обновления (в котором поставщик записывает изменения в источнике данных при вызове метода **обновление** метод), вызов **AddNew** метод без аргументов наборов  **EditMode** свойства **adEditAdd.** Поставщик кэширует изменения значений поля локально. Вызов **обновление** метод отправляет новую запись в базу данных и сбрасывает **EditMode** свойства **как таковые.** Если передать *списка полей* и *значения* аргументы, ADO немедленно отправляет новую запись в базу данных (не **обновление** вызов необходим); **EditMode**  не изменяет значение свойства (**как таковые**).  
  
 В пакетном режиме обновления вызвав **AddNew** метод без аргументов наборов **EditMode** свойства **adEditAdd**. Поставщик кэширует изменения значений поля локально. Вызов **обновление** метод добавляет новую запись в текущий **записей** и сбрасывает **EditMode** свойства **как таковые**, но Поставщик не учет изменений в основную базу данных, пока не будет вызван **UpdateBatch** метод. Если передать *списка полей* и *значения* аргументы, ADO отправляет новую запись для поставщика для хранения в кэше; необходимо вызвать **UpdateBatch** метод для учета нового запись в основной базе данных. Дополнительные сведения о **обновление** и **UpdateBatch**, в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).
