---
title: Другие заметки (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f379a046b73dbd073c7e0f01b5c41be7589964d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101956"
---
# <a name="other-annotations-sqlxml-40"></a>Другие заметки (SQLXML 4.0)
  Помимо заметок, описанных в предыдущих подразделах этого раздела, массовая загрузка XML интерпретирует ниже приведенные заметки.  
  
 `sql:id-prefix`  
 Если схема указывает префиксы к XML-данным, то перед передачей данных в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] массовая загрузка XML удаляет эти префиксы.  
  
 `sql:use-cdata`  
 Массовая загрузка XML считывает текст, хранящийся в разделах CDATA, и отправляет его в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:url-encode`  
 Массовая загрузка XML не поддерживает эту заметку. Например, в выходных XML-данных нельзя указать URL-адрес и ожидать, что массовая загрузка XML считает данные из местоположения и сохранит их в базе данных.  
  
 `sql:is-mapping-schema`  
 Массовая загрузка XML не поддерживает ни эту заметку, ни `sql:id`.  
  
> [!NOTE]  
>  Массовая загрузка XML не поддерживает встроенные схемы сопоставления.  
  
 `sql:key-fields`  
 Массовая загрузка XML никогда не обрабатывает эту заметку.  
  
## <a name="see-also"></a>См. также  
 [Интерпретация заметки &#40;SQLXML 4.0&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  