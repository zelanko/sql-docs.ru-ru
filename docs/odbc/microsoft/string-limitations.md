---
title: Строка, ограничения | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948765"
---
# <a name="string-limitations"></a>Ограничения строк
Максимальная длина инструкции SQL-строки составляет 65 000 символов.  
  
 Если используется драйвер Microsoft Access, поддерживаются только SQL-92 строковых констант (одиночные кавычки не двойные кавычки).  
  
 Символ вертикальной черты (&#124;) не может использоваться в строке ли символ заключен в кавычки назад или нет.  
  
 Для максимальной совместимости приложений должна передавать параметры строки, а не заключено в кавычки строки для передачи.
