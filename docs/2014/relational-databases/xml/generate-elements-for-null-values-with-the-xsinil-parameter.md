---
title: Создание элементов для значений NULL с помощью параметра XSINIL | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a99a1ab6c4c051f0a5d063b358b2ad9dbb5e5c08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102404"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Создание элементов для значений NULL с помощью параметра XSINIL
  Директива **ELEMENTS** формирует XML, в котором каждое значение в столбце соответствует элементу XML. Если этот значение в столбце имеет значение NULL, элемент не добавляется. Указав в директиве ELEMENTS необязательный параметр **XSINIL** , можно запросить, чтобы для значений NULL тоже создавались элементы. В этом случае атрибут **xsi:nil** этого элемента имеет значение TRUE для каждого значения NULL в столбце.  
  
## <a name="see-also"></a>См. также  
 [Использование с RAW Mode для FOR XML](use-raw-mode-with-for-xml.md)  
  
  
