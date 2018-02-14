---
title: "Создание встроенных схем XDR | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a907df120142a65c7552da2b66d3b16485e014fa
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="generate-an-inline-xdr-schema"></a>Создание встроенных схем XDR
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
При указании в предложении FOR XML директивы **XMLDATA** вместе с результатом запроса возвращается встроенная XDR-схема. Однако XDR-схема не поддерживает какие-либо новые типы данных и другие усовершенствования в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях. Вместо этого с помощью директивы [XMLSCHEMA](../../relational-databases/xml/generate-an-inline-xsd-schema.md)можно запрашивать встроенную XSD-схему.  
  
> [!IMPORTANT]  
>  Директива XMLDATA для параметра XML FOR является устаревшей. В режимах RAW и AUTO следует использовать создание XSD-схем. В режиме EXPLICIT для директивы XMLDATA замены нет. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Также имейте в виду следующие сведения, касающиеся поддержки встроенной XSD-схемы:  
  
-   Если результат выполнения запроса FOR XML включает в себя столбцы типа **xml** и при этом запрашивается встроенная XSD-схема, будет возвращено сообщение об ошибке. Встроенная XSD-схема не поддерживает эти типы данных.  
  
-   Типы данных **(n)varchar(max)** и **(n)varbinary(max)** будут сопоставлены с данными типа **(n)varchar(n)** и **varbinary(n)**соответственно.  
  
-   При уровне совместимости 90 или выше значения типа **timestamp** рассматриваются как данные типа **varbinary(8)** , обрабатываются как двоичные данные, а результат обработки возвращается в следующем виде:  
  
    -   Если указан параметр **binary base64** , используется кодировка Base 64.  
  
    -   Если параметр **binary base64** не указан, используется кодировка URL в режиме AUTO.  
  
  
