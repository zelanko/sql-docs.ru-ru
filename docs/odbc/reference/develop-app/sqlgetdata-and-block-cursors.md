---
title: СЗЛГетДата и Блок Курзоры (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b60d7093552b8f1dbed87d9ad8840ddb5a9e0799
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299754"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData и блочные курсоры
**SLGetData** работает на одном столбце одной строки и не может получить массив, содержащий данные из нескольких строк. Это объясняется тем, что основное использование **S'LGetData** заключается в том, чтобы получать длинные данные по частям, и нет никаких оснований делать это более чем на одну строку за один раз.  
  
 Для использования **s'LGetData** с помощью курсора блока приложение сначала вызывает **S'LSetPos,** чтобы позиционировать курсор на одном ряду. Затем он вызывает **s'LGetData** для столбца в этой строке. Однако такое поведение не является обязательным. Чтобы определить, поддерживает ли драйвер использование **S'LGetData** с помощью курсоров блоков, приложение вызывает **s'LGetInfo** с опцией SQL_GETDATA_EXTENSIONS.
