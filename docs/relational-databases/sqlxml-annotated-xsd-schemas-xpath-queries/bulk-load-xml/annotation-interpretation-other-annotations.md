---
title: "Другие заметки (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
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
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c66f2bb5bb89e2d8ac46fb8e6d20a8c79a49b27
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="annotation-interpretation---other-annotations"></a>Интерпретация заметки - других заметок
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Помимо заметок, описанных в предыдущих подразделах этого раздела Массовая загрузка XML интерпретирует эти другие аннотации следующим образом:  
  
 **SQL: ID-префикс**  
 Если схема указывает префиксы к XML-данным, то перед передачей данных в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] массовая загрузка XML удаляет эти префиксы.  
  
 **SQL: USE-cdata**  
 Массовая загрузка XML считывает текст, хранящийся в разделах CDATA, и отправляет его в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **заметки SQL: URL-кодирование**  
 Массовая загрузка XML не поддерживает эту заметку. Например, в выходных XML-данных нельзя указать URL-адрес и ожидать, что массовая загрузка XML считает данные из местоположения и сохранит их в базе данных.  
  
 **SQL: является mapping-schema**  
 Массовая загрузка XML не поддерживает ни эту заметку, ни **sql:id**.  
  
> [!NOTE]  
>  Массовая загрузка XML не поддерживает встроенные схемы сопоставления.  
  
 **SQL: Key-поля**  
 Массовая загрузка XML никогда не обрабатывает эту заметку.  
  
## <a name="see-also"></a>См. также:  
 [Интерпретация заметки &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
