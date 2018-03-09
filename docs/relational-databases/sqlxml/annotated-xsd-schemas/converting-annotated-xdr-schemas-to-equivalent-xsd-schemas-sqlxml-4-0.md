---
title: "Преобразование схем XDR в эквивалентные схемы XSD (SQLXML 4.0) с заметками | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b18c3effc0aa7177c34d52cf321f0f1cc046270d
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a>Преобразование схем XDR с заметками в эквивалентные схемы XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Язык определения схем XML (XSD) пришел на смену языку определения схем с сокращенными XML-данными (XDR). После ввода в действие поддержки XSD в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 предполагается, что новые схемы с заметками должны создаваться при помощи XSD. SQLXML 4.0 включает средство преобразования XDR в XSD, которое создано для предоставления помощи пользователю в преобразовании существующих схем XDR с заметками в равнозначные схемы XSD.  
  
> [!IMPORTANT]  
>  Это средство рекомендуется использовать только для преобразования схем XDR в XSD в целях их применения с SQLXML 4.0. Это не следует считать средством преобразования XDR в XSD общего назначения. Преобразованные схемы XSD могут не действовать в полном соответствии с исходными схемами XDR, будучи используемыми в других средах.  
  
 Если входной XDR-файл задает в XML-декларации кодировку, она становится кодировкой создаваемого выходного XSD-файла.  
  
 Средство преобразования (Cvtschema.exe) установлено в папке Program Files\SQLXML 4.0\bin и исполняется в командной строке.  
  
 Далее представлен общий синтаксис:  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 Где:  
  
 XDRFileName  
 Имя XDR-файла, который необходимо преобразовать в XSD. Это средство читает входной XDR-файл и создает выходной XSD-файл в текущем рабочем каталоге. Если текущий файл имеет расширение XDR или XML, выходной XSD-файл создается с тем же именем, но с расширением XSD. Если расширение имени входного файла, отличные от XML или .xdr (или если расширение не указано), выходной файл создается с тем же именем и расширение XSD-файл добавляется к имени входного файла. Например, если именем входного XDR-файла является SampleFile.abc, то полученный XSD-файл сохраняется как SampleFile.abc.xsd.  
  
 -y  
 Перезаписывает существующий XSD-файл XSD-файлом, созданным средством преобразования (необязательно). Если этот флаг не указан, в этом средстве происходит вывод приглашения для пользователя, которое позволяет указать, следует ли переписать существующий XSD-файл и изменить имя выходного файла.  
  
 -w  
 Возвращает некритичные предупреждения, сформированные этим средством в процессе преобразования (необязательно). По умолчанию это средство отображает только сообщения, относящиеся к неустранимым ошибкам.  
  
 -?  
 Возвращает список параметров, которые можно задать, используя **cvtschema**, а также описание.  
  
## <a name="see-also"></a>См. также  
 [Сопоставление типов данных XSD для типов данных XPath &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)   
 [Заметки XSD &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
