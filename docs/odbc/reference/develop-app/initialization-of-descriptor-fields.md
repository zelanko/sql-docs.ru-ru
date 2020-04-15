---
title: Инициализация полей дескрипторов Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300124"
---
# <a name="initialization-of-descriptor-fields"></a>Инициализация полей дескриптора
При выделении дескриптора строки приложения его поля получают начальные значения, указанные в [S'LSetDescField.](../../../odbc/reference/syntax/sqlsetdescfield-function.md) Начальное значение SQL_DESC_TYPE поля является SQL_DEFAULT. Это обеспечивает стандартную обработку данных базы данных для представления в приложение. Приложение может указать различную обработку данных, установив поля записи дескриптора.  
  
 Начальное значение SQL_DESC_ARRAY_SIZE в заголовке дескриптора 1. Приложение может изменить это поле, чтобы включить многороут извлечение.  
  
 Понятие значения по умолчанию не действует для полей IRD. Приложение может получить доступ к полям IRD только в том случае, если с ним связано подготовленное или выполненное заявление.  
  
 Некоторые поля IPD определяются только после того, как IPD был автоматически заселен водителем. Если нет, то они не определены. Это SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED и SQL_DESC_LOCAL_TYPE_NAME.
