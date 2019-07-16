---
title: Другие заметки (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
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
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a9a965ee5772ea3c2855a08d838c1d89da343e9d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066865"
---
# <a name="annotation-interpretation---other-annotations"></a>Интерпретация заметки — прочие заметки
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Помимо заметок, описанных в предыдущих подразделах этого раздела, массовая загрузка XML интерпретирует ниже приведенные заметки.  
  
 **sql:id-prefix**  
 Если схема указывает префиксы к XML-данным, то перед передачей данных в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]массовая загрузка XML удаляет эти префиксы.  
  
 **SQL: USE-cdata**  
 Массовая загрузка XML считывает текст, хранящийся в разделах CDATA, и отправляет его в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **заметки SQL: URL-кодирование**  
 Массовая загрузка XML не поддерживает эту заметку. Например, в выходных XML-данных нельзя указать URL-адрес и ожидать, что массовая загрузка XML считает данные из местоположения и сохранит их в базе данных.  
  
 **sql:is-mapping-schema**  
 Массовая загрузка XML не поддерживает ни эту заметку, ни **sql:id**.  
  
> [!NOTE]  
>  Массовая загрузка XML не поддерживает встроенные схемы сопоставления.  
  
 **SQL: Key-поля**  
 Массовая загрузка XML никогда не обрабатывает эту заметку.  
  
## <a name="see-also"></a>См. также  
 [Интерпретация заметки &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
