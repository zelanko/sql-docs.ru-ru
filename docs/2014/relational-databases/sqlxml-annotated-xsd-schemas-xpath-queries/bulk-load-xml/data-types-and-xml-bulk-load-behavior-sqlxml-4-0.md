---
title: Типы данных и XML массового режима загрузки (SQLXML 4.0) | Документы Microsoft
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
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 752dca45eb12e4148ab407b578d0f4161444ece9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097904"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Типы данных и массовая загрузка XML (SQLXML 4.0)
  Типы данных, заданные в схеме сопоставления (тип XSD, XDR и `sql:datatype`), как правило, пропускаются, за исключением следующих случаев.  
  
 В XSD.  
  
-   Если данные имеют тип `dateTime` или `time`, необходимо задать `sql:datatype`, поскольку в ходе массовой загрузки XML выполняется преобразование данных перед их отправкой в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Когда выполняется Массовая загрузка в столбец `uniqueidentifier` введите в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и значение XSD представляет идентификатор GUID, который включает фигурные скобки ({и}), вы должны указать **SQL: DataType = «uniqueidentifier»** Чтобы удалить скобки перед значение равно вставляемое в столбец. Если атрибут `sql:datatype` не задан, то значение передается вместе с фигурными скобками и вставка завершается ошибкой.  
  
 Дополнительные сведения о `sql:datatype`, в разделе [преобразований типов данных и заметка SQL: DataType &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XDR:  
  
-   Если `dt:type` имеет тип `datetime`, `time`, `dateTime.tz` или `time.tz`, необходимо задать типы данных `dt:type` и `sql:datatype`, поскольку при массовой загрузке XML выполняется преобразование данных перед отправкой в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Если данные XML имеет тип `uuid`, `sql:datatype` должен быть указан; **DT: Type = «uuid»** также является обязательным, если данные являются строковыми. Если атрибут `dt:uuid` не задан, то при массовой загрузке XML строки с фигурными скобками принимаются (фигурные скобки при необходимости удаляются).  
  
-   Если данные XML имеют тип `bin.base64` или `bin.hex`, необходимо указать тип данных XML с атрибутом `dt:type`. В таком случае при массовой загрузке XML данные загружаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в шестнадцатеричном представлении.  
  
  