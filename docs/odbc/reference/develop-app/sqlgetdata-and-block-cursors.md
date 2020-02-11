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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107402"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData и блочные курсоры
**SQLGetData** работает с одним столбцом одной строки и не может получить массив, содержащий данные из нескольких строк. Это связано с тем, что основное использование **SQLGetData** заключается в выборке длинных данных в частях, и нет причин делать это для более чем одной строки за раз.  
  
 Чтобы использовать **SQLGetData** с блочным курсором, приложение сначала вызывает функцию **SQLSetPos** для позиционирования курсора в одной строке. Затем он вызывает **SQLGetData** для столбца в этой строке. Однако это необязательное поведение. Чтобы определить, поддерживает ли драйвер использование **SQLGetData** с блочными курсорами, приложение вызывает **SQLGetInfo** с параметром SQL_GETDATA_EXTENSIONS.
