---
description: Ограничения строк
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
ms.openlocfilehash: c21d86a3c626ced52c6b7915d3cfbd9322fb596e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449136"
---
# <a name="string-limitations"></a>Ограничения строк
Максимальная длина строки инструкции SQL — 65 000 символов.  
  
 При использовании драйвера Microsoft Access поддерживаются только строковые константы SQL-92 (с одиночными кавычками, а не двойные кавычки).  
  
 Символ вертикальной черты (&#124;) нельзя использовать в строке, независимо от того, заключен символ в обратные кавычки или нет.  
  
 Для обеспечения максимальной совместимости приложения должны передавать строки в параметрах вместо передачи строк в кавычках.
