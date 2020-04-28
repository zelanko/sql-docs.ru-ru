---
title: Дескрипторы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca8299daae744fb9398ed6ffc99c838ce8edff48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305905"
---
# <a name="descriptors"></a>Дескрипторы
Дескриптор дескриптора ссылается на структуру данных, содержащую сведения о столбцах или динамических параметрах.  
  
 Функции ODBC, которые работают с данными столбцов и параметров, неявно устанавливают и извлекают поля дескриптора. Например, при вызове **SQLBindCol** для привязки данных столбца задаются поля дескриптора, которые полностью описывают привязку. При вызове **SQLColAttribute** для описания данных столбца возвращаются данные, хранящиеся в полях дескриптора.  
  
 Приложению, вызывающему функции ODBC, не нужно беспокоиться о себе с дескрипторами. Ни одна операция с базой данных не требует от приложения получить прямой доступ к дескрипторам. Однако для некоторых приложений получение прямого доступа к дескрипторам упрощает многие операции. Например, прямой доступ к дескрипторам предоставляет способ повторной привязки данных столбца, что может быть более эффективным, чем повторный вызов **SQLBindCol** .  
  
> [!NOTE]  
>  Физическое представление дескриптора не определено. Приложения получают прямой доступ к дескриптору только путем обработки его полей путем вызова функций ODBC с помощью дескриптора дескриптора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы дескрипторов](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Выделение и освобождение дескрипторов](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Получение и установка полей дескриптора](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
