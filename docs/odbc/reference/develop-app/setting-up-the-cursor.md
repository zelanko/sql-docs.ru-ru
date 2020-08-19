---
description: Настройка курсора
title: Настройка курсора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 307245dc403167f5bd857005f084ed22498d3ee8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424586"
---
# <a name="setting-up-the-cursor"></a>Настройка курсора
Приложение может указать тип курсора перед выполнением инструкции, которая создает результирующий набор. Это достигается с помощью атрибута оператора SQL_ATTR_CURSOR_TYPE. Если в приложении явно не указан тип, будет использоваться однонаправленный курсор. Для получения смешанного курсора приложение указывает курсор, управляемый набором ключей, но объявляет размер набора ключей меньше, чем размер результирующих наборов.  
  
 Для управляемых набором ключей и смешанных курсоров в приложении также можно указать размер набора ключей. Это достигается с помощью атрибута оператора SQL_ATTR_KEYSET_SIZE. Если размер набора ключей равен 0 (по умолчанию), то размер набора ключей устанавливается в результирующий набор и используется курсор, управляемый набором ключей. Размер набора ключей можно изменить после открытия курсора.  
  
 Приложение также может задавать размер набора строк; Дополнительные сведения см. выше в разделе [Использование блочных курсоров](../../../odbc/reference/develop-app/using-block-cursors.md).
