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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7faab41bd52397ac0d352e04a9ec153571e93f1e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948765"
---
# <a name="string-limitations"></a>Ограничения строк
Максимальная длина строки инструкции SQL — 65 000 символов.  
  
 При использовании драйвера Microsoft Access поддерживаются только строковые константы SQL-92 (с одиночными кавычками, а не двойные кавычки).  
  
 Символ вертикальной черты (&#124;) нельзя использовать в строке, независимо от того, заключен символ в обратные кавычки или нет.  
  
 Для обеспечения максимальной совместимости приложения должны передавать строки в параметрах вместо передачи строк в кавычках.
