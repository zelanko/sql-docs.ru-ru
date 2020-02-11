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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f2138a5f8417fc9156c916719e96d707b9a29de9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040010"
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
