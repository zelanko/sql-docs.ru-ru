---
title: Ограничения строк | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306065"
---
# <a name="string-limitations"></a>Ограничения строк
Максимальная длина строки инструкции SQL — 65 000 символов.  
  
 При использовании драйвера Microsoft Access поддерживаются только строковые константы SQL-92 (с одиночными кавычками, а не двойные кавычки).  
  
 Символ вертикальной черты (&#124;) нельзя использовать в строке, независимо от того, заключен символ в обратные кавычки или нет.  
  
 Для обеспечения максимальной совместимости приложения должны передавать строки в параметрах вместо передачи строк в кавычках.
