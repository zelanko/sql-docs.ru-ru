---
title: Типы данных экземпляра CDC Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c2a277f030fc948ef63a82a7ff18c5dbe9fc5a1f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193616"
---
# <a name="oracle-cdc-instance-data-types"></a>Типы данных экземпляра CDC Oracle
  Экземпляр Oracle CDC поддерживает большинство типов данных Oracle. В следующих разделах описаны поддерживаемые и неподдерживаемые типы данных.  
  
## <a name="supported-data-types"></a>Поддерживаемые типы данных  
 В следующей таблице указаны типы данных Oracle, для которых можно проводить отслеживание изменений, а также их сопоставление по умолчанию с типами данных SQL Server в таблицах изменений. При добавлении экземпляра отслеживания для таблицы из исходной базы данных Oracle можно переопределить некоторые из этих сопоставлений.  
  
|Тип данных базы данных Oracle|Тип данных SQL Server|  
|-------------------------------|--------------------------|  
|BINARY_FLOAT|real|  
|BINARY_DOUBLE|FLOAT|  
|CHAR|NVARCHAR|  
|DATE|DATETIME|  
|FLOAT|FLOAT|  
|INT|NUMERIC (38)|  
|INTERVAL|DATETIME|  
|NCHAR|NVARCHAR|  
|NUMBER|FLOAT|  
|NAVARCHAR2|NVARCHAR|  
|RAW|VARBINARY|  
|real|FLOAT|  
|TIMESTAMP|DATETIME2|  
|TIMESTAMP WITH TIME ZONE|VARCHAR (37)|  
|TIMESTAMP WITH LOCAL TIME ZONE|VARCHAR (37)|  
|VARCHAR2|VARCHAR|  
|XMLTYPE|NVARCHAR (MAX)|  
  
## <a name="non-supported-data-types"></a>Неподдерживаемые типы данных  
 Для исходных таблиц Oracle со столбцами следующих типов данных Oracle отслеживание изменений проводиться не может. Отслеживаемые столбцы с данными этого типа будут показаны как столбцы со значениями NULL, однако изменения их значений будут указываться в маске изменения отслеживаемых таблиц.  
  
-   LONG  
  
-   XMLTYPE  
  
-   BLOB  
  
-   CLOB  
  
 Для исходных таблиц Oracle со столбцами следующих типов данных Oracle отслеживание изменений проводиться не может.  
  
-   BFILE  
  
-   ROWID  
  
-   REF  
  
-   UROWID  
  
-   Вложенная таблица  
  
 Если в таблице имеются данные этих типов, средство интеллектуального анализа журнала не сможет получить какие-либо данные ни для одного столбца этой таблицы.  
  
-   Определяемые пользователем типы данных  
  
-   VARRAY  
  
## <a name="see-also"></a>См. также  
 [Конструктор системы отслеживания измененных данных для Oracle компании attunity](change-data-capture-designer-for-oracle-by-attunity.md)   
 [Экземпляр CDC Oracle](the-oracle-cdc-instance.md)  
  
  