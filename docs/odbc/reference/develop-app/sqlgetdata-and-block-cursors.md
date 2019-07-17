---
title: SQLGetData и блочные курсоры | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4841d8d923ff73d187569df3d7f9e29daf0f4e48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107402"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData и блочные курсоры
**SQLGetData** работает по одному столбцу из одной строки и не может получить массив, содержащий данные из нескольких строк. Это так, как использовать основной **SQLGetData** — выборка данных long в части, и практически не причин для этого для более чем одной строке за раз.  
  
 Чтобы использовать **SQLGetData** с блочными, приложение сначала вызывает **SQLSetPos** для позиционирования курсора на одну строку. Затем он вызывает **SQLGetData** для столбца в этой строке. Однако такое поведение является необязательным. Чтобы определить, если драйвер поддерживает использование **SQLGetData** с блочными курсорами, приложение вызывает **SQLGetInfo** с параметром SQL_GETDATA_EXTENSIONS.
