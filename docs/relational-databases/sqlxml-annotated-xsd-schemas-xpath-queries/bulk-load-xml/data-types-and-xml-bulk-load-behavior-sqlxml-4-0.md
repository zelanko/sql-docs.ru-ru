---
title: "Типы данных и XML массового режима загрузки (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d5e25e9d3a2df2e15c2dc9bf86d6d90acd1d450
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Типы данных и массовая загрузка XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Типы данных, указанных в схеме сопоставления (тип XSD или XDR и **SQL: DataType**) обычно учитываются, за исключением следующих случаев:  
  
 В XSD.  
  
-   Если тип является **dateTime** или **время**, необходимо указать **SQL: DataType** так, как Массовая загрузка XML выполняется преобразование данных до их отправки в корпорацию Майкрософт [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Когда выполняется Массовая загрузка в столбец **uniqueidentifier** введите [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и значение XSD представляет идентификатор GUID, который включает фигурные скобки ({и}), вы должны указать **SQL: DataType = «uniqueidentifier»** для Удалите фигурные скобки перед вставкой значения в столбце. Если **SQL: DataType** не указан, значение пересылается с фигурными скобками и вставка завершается ошибкой.  
  
 Дополнительные сведения о **SQL: DataType**, в разделе [преобразований типов данных и заметка SQL: DataType &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XDR:  
  
-   Если **DT: Type** — **datetime**, **время**, **dateTime.tz**, или **time.tz**, должны быть указаны **DT: Type** и **SQL: DataType** типы данных, поскольку Массовая загрузка XML выполняется преобразование данных перед отправкой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Если данные XML имеет тип **uuid**, **SQL: DataType** должен быть указан; **DT: Type = «uuid»** также является обязательным, если данные являются строковыми. Если вы не укажете **dt:uuid**, Массовая загрузка XML принимает строки с фигурными скобками (и при необходимости удаляются).  
  
-   Если XML-данные **bin.base64** или **bin.hex**, необходимо указать тип данных XML с **DT: Type**. В таком случае при массовой загрузке XML данные загружаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в шестнадцатеричном представлении.  
  
  
