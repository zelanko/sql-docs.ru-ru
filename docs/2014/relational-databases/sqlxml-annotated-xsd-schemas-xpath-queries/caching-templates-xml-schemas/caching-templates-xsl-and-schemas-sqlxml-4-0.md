---
title: Кэширование шаблонов, XSL и схем (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dea5fe9357bdc5431a5a787e1a020832fed35955
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103044"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Кэширование шаблонов, XSL и схем (SQLXML 4.0)
  Для повышения производительности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 поддерживает кэширование шаблонов, XSL и схем.  
  
 Все файлы схем, шаблонов и XSL-файлы (кроме файлов с местонахождением http:// или ftp://) кэшируются. Кэшированные файлы остаются в памяти, пока процесс выполняется. При завершении процесса содержимое кэша уничтожается. Поэтому, если в запросе выполняется один процесс, выигрыш от кэширования может быть незначителен.  
  
 Подразделы этого раздела содержат дополнительные сведения о кэшировании.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Кэширование шаблонов &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)  
 Описывается кэширование шаблонов и приводится соответствующий раздел реестра.  
  
 [Кэширование XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
 Описывается кэширование XSL и приводится соответствующий раздел реестра.  
  
 [Кэширование схем &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
 Обсуждаются вопросы параллельной установки SQLXML, связанные с кэшированием схем, и приводятся соответствующие разделы реестра.  
  
  
