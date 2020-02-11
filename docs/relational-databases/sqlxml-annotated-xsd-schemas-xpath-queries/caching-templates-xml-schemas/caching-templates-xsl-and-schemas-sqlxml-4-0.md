---
title: Шаблоны кэширования, XSL и схемы (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6201cd2cf27e48f5a5101c3bdcda4da644756a13
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75246690"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Кэширование шаблонов, XSL и схем (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Для повышения производительности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 поддерживает кэширование шаблонов, XSL и схем.  
  
 Кэшируются все схемы, шаблоны и файлы XSL (кроме файлов из расположения https://или ftp://). Кэшированные файлы остаются в памяти, пока процесс выполняется. При завершении процесса содержимое кэша уничтожается. Поэтому, если в запросе выполняется один процесс, выигрыш от кэширования может быть незначителен.  
  
 Подразделы этого раздела содержат дополнительные сведения о кэшировании.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Кэширование шаблонов &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 Описывается кэширование шаблонов и приводится соответствующий раздел реестра.  
  
 [Кэширование XSL &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 Описывается кэширование XSL и приводится соответствующий раздел реестра.  
  
 [Кэширование схемы &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 Обсуждаются вопросы параллельной установки SQLXML, связанные с кэшированием схем, и приводятся соответствующие разделы реестра.  
  
  
