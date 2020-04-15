---
title: Ограничения струнных строк Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306065"
---
# <a name="string-limitations"></a>Ограничения строк
Максимальная длина строки оператора S'L составляет 65 000 символов.  
  
 При использовании драйвера Microsoft Access поддерживаются только константы строки S-L-92 (с одними кавычками, а не двойными кавычками).  
  
 Символ трубы (&#124;) не может быть использован в строке, независимо от того, заключен ли символ в задние кавычки или нет.  
  
 Для максимальной совместимости приложения должны проходить строки по параметрам, а не передавать цитируемые строки.
