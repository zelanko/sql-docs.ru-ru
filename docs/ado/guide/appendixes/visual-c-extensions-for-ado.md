---
title: Расширения Visual C++ для ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca21e976783a10a738488762e382982e4fd8fd8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747682"
---
# <a name="visual-c-extensions"></a>Расширения Visual C++
Предпочтительный способ программирования ADO в Visual C++ использует **#import** директивы, как описано в [Microsoft Visual C++ ADO программирования](../../../ado/guide/appendixes/visual-c-ado-programming.md). Тем не менее, более ранних версиях ADO в состав альтернативный способ программирования на языке Visual C++: расширения Visual C++. В данном разделе описываются эту функцию для тех, кто должен поддерживать код расширений Visual C++, но новый код ADO должны быть написаны с помощью #**импорта**.

 Одно из самых трудоемких заданий Visual C++ программистов начертание шрифта при извлечении данных с помощью ADO преобразует данные возвращаются как тип данных VARIANT в тип данных C++ и последующее сохранение преобразованных данных в классе или структуре. Помимо громоздким, извлечение данных C++ с помощью типа данных VARIANT снижает производительность.

 ADO предоставляет интерфейс, который поддерживает получение данных в собственные типы данных C/C++, минуя VARIANT, а также макросы препроцессора, которые упрощают использование интерфейса. Результат — это гибкий инструмент, который проще в использовании и имеет отличную производительность.

 Распространенный сценарий клиента C/C++ — для привязки к записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) C/C++ структура или класс, содержащий собственные типы C/C++. При работе через вариантов, это требует написания кода преобразования из типа VARIANT в собственные типы C/C++. Расширения Visual C++ для ADO предназначены поэтому данную ситуацию намного проще для программистов Visual C++.

 Дополнительные сведения о расширениях Visual C++ для ADO см.

-   [Использование расширений Visual C++ для ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Заголовок расширений Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [ADO с образец расширения Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>См. также
 [Индекс синтаксиса Visual C++ для модели COM ADO для](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [образец расширения Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [использование расширений Visual C++](../../../ado/guide/appendixes/using-visual-c-extensions.md) [заголовок расширений Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)
