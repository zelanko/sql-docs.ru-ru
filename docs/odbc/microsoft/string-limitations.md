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
manager: craigg
ms.openlocfilehash: 003cd318d6db54c7547375219805c63cfc4ce249
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63269867"
---
# <a name="string-limitations"></a>Ограничения строк
Максимальная длина инструкции SQL-строки составляет 65 000 символов.  
  
 Если используется драйвер Microsoft Access, поддерживаются только SQL-92 строковых констант (одиночные кавычки не двойные кавычки).  
  
 Символ вертикальной черты (&#124;) не может использоваться в строке ли символ заключен в кавычки назад или нет.  
  
 Для максимальной совместимости приложений должна передавать параметры строки, а не заключено в кавычки строки для передачи.
