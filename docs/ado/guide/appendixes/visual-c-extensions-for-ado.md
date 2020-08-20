---
description: Расширения Visual C++ для ADO
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f9fa962d4710811cf376634dcc299707f6b0e654
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453936"
---
# <a name="visual-c-extensions-for-ado"></a>Расширения Visual C++ для ADO
Предпочтительный метод программирования ADO с Visual C++ использует директиву **#import** , как описано в [Microsoft Visual C++ программировании ADO](../../../ado/guide/appendixes/visual-c-ado-programming.md). Однако более ранние версии ADO поставляются с альтернативным методом программирования с использованием Visual C++: расширений Visual C++. В этом разделе описывается эта функция для тех, кто должен поддерживать код расширений Visual C++, но новый код ADO должен быть написан с помощью директивы #**Import**.

 Одно из самых утомительных заданий Visual C++ программистов при извлечении данных с помощью ADO — преобразование данных, возвращаемых в тип данных VARIANT, в типы данных C++, а затем сохранение преобразованных данных в классе или структуре. В дополнение к громоздким, получение данных C++ через тип данных VARIANT уменьшает производительность.

 ADO предоставляет интерфейс, который поддерживает извлечение данных в собственные типы данных C/C++ без использования варианта, а также предоставляет макросы препроцессора, упрощающие использование интерфейса. Результатом является гибкое средство, которое проще в использовании и имеет высокую производительность.

 Распространенным сценарием клиента C/C++ является привязка записи в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md) к структуре C/c++ или к классу, содержащему собственные типы C/c++. При переходе по вариантам это включает запись кода преобразования из типа VARIANT в собственные типы C/C++. Расширения Visual C++ для ADO предназначены для упрощения этого сценария Visual C++ программиста.

 Дополнительные сведения о расширениях Visual C++ для ADO см. в следующих разделах.

-   [Использование расширений Visual C++ для ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Заголовок расширений Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [Пример модулей ADO с расширениями Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>См. также:
 [Visual C++ный индекс синтаксиса ADO для расширений COM-](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C++ пример](../../../ado/guide/appendixes/visual-c-extensions-example.md) [с использованием](../../../ado/guide/appendixes/using-visual-c-extensions.md) [заголовка Visual C++ расширений](../../../ado/guide/appendixes/visual-c-extensions-header.md) Visual C++ Extensions
