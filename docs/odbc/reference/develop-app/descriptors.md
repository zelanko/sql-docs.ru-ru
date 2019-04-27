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
manager: craigg
ms.openlocfilehash: d50ce0c2023e187d63d08aa862398d18dc188fd1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62744231"
---
# <a name="descriptors"></a>Дескрипторы
Дескриптор дескриптора ссылается на структуру данных, которая содержит информацию о столбцах или динамических параметров.  
  
 Функции ODBC, которые работают с параметров и столбцов данных, неявно задание и получение поля дескриптора. Например, если **SQLBindCol** вызывается для привязки данных в столбце, он задает поля дескриптора, полностью описывающие привязку. Когда **SQLColAttribute** вызывается для описания столбцов данных, он возвращает данные, хранящиеся в поля дескриптора.  
  
 Вызов функций ODBC приложение требуется не связан с дескрипторами. Ни одна из операций базы данных требует, что приложение прямого доступа к дескрипторам. Тем не менее для некоторых приложений получения прямого доступа к дескрипторам упрощает выполнение многих операций. Например, прямой доступ к дескрипторам позволяет выполнять повторную привязку данных в столбце, который может быть более эффективным, чем вызов **SQLBindCol** еще раз.  
  
> [!NOTE]  
>  Физическое представление дескриптора не определен. Приложениям получать непосредственный доступ к дескриптор только управляя его поля путем вызова функции ODBC с помощью дескриптора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы дескрипторов](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Выделение и освобождение дескрипторов](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Получение и установка полей дескриптора](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
