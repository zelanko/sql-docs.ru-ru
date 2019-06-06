---
title: Расширения Visual C++ для ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
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
manager: jroth
ms.openlocfilehash: ccd783bdb7bf266bfdc83c3a02520345d707ceea
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702631"
---
# <a name="visual-c-extensions-for-ado"></a>Расширения Visual C++ для ADO
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
