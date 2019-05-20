---
title: Типы данных экземпляра CDC Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f3714d58bea5ce8751f2b520a6c4f75353f48a64
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728775"
---
# <a name="oracle-cdc-instance-data-types"></a>Типы данных экземпляра CDC Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
## <a name="see-also"></a>См. также:  
 [Конструктор системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-designer-for-oracle-by-attunity.md)   
 [Экземпляр CDC Oracle](../../integration-services/change-data-capture/the-oracle-cdc-instance.md)  
  
  
