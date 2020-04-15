---
title: Дескрипторы Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305905"
---
# <a name="descriptors"></a>Дескрипторы
Ручка дескриптора относится к структуре данных, которая содержит информацию о столбцах или динамических параметрах.  
  
 Функции ODBC, работающие на столбцах и параметрах данных, неявно устанавливают и извлекают поля дескриптора. Например, когда **s'LBindCol** вызывается для связывания данных столбцов, он устанавливает полей дескриптора, которые полностью описывают привязку. Когда для описания данных столбцов вызывается **s'LColAttribute,** он возвращает данные, хранящиеся в полях дескрипторов.  
  
 Приложение, вызывая функции ODBC, не должно касаться дескрипторов. Никакая операция базы данных не требует, чтобы приложение получило прямой доступ к дескрипторам. Однако для некоторых приложений получение прямого доступа к дескрипторам упрощает многие операции. Например, прямой доступ к дескрипторам позволяет перезавязать данные столбцов, что может быть более эффективным, чем вызов **S'LBindCol** снова.  
  
> [!NOTE]  
>  Физическое представление дескриптора не определено. Приложения получают прямой доступ к дескриптору только путем манипулирования его полями, вызывая функции ODBC с помощью дескриптора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы дескрипторов](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Выделение и освобождение дескрипторов](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Получение и установка полей дескриптора](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
