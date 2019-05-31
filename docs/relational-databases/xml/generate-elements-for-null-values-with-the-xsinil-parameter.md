---
title: Создание элементов для значений NULL с помощью параметра XSINIL | Документация Майкрософт
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0889de0a7525e0e5a7ea91ba169011aaf4e341a
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175174"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Создание элементов для значений NULL с помощью параметра XSINIL

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Директива **ELEMENTS** формирует XML, в котором каждое значение в столбце соответствует элементу XML. По умолчанию, если это значение в столбце равно NULL, элемент не добавляется. Однако, указав в директиве ELEMENTS необязательный параметр **XSINIL**, можно запросить, чтобы для значений NULL тоже создавались элементы. В этом случае атрибут **xsi:nil** этого элемента имеет значение TRUE для каждого значения NULL в столбце.  
  
## <a name="see-also"></a>См. также:

[Использование RAW Mode с FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

[SELECT — предложение FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
