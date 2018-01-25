---
title: "Канонические формы и ограничения шаблона | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f6682717a70bc98358a3cb010f38b773c0b44ca
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="canonical-forms-and-pattern-restrictions"></a>Канонические формы и ограничения шаблона
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Аспект шаблона XSD позволяет вводить ограничение лексического пространства простых типов. Когда ограничение шаблона наложено на тип, для которого есть больше одного возможного лексического представления, некоторые значения могут вызвать непредвиденное поведение в ходе проверки.  
  
 Такое поведение возникает, потому что лексические представления этих значений не сохраняются в базе данных. Поэтому значения будут преобразованы к их каноническим представлениям при сериализации вывода. Если документ содержит значение, каноническая форма которого не соответствует ограничению шаблона для его типа, то документ будет отклонен, если пользователь попытается вставить его повторно.  
  
 Чтобы это предотвратить, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отклоняет любой документ XML, содержащий значения, которые не могут быть повторно вставлены из-за нарушения ограничений шаблона их каноническими формами. Например, значение "33.000" не пройдет проверку относительно типа, производного от **xs:decimal** с ограничением шаблона "33.\\.0+". Хотя «33.000» соответствует этому шаблону, его каноническая форма «33» шаблону не соответствует.  
  
 Поэтому следует быть внимательными при применении аспектов шаблона к типам, производным от следующих типов-примитивов: **boolean**, **decimal**, **float**, **double**, **dateTime**, **time**, **date**, **hexBinary**и **base64Binary**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдаст предупреждение при добавлении любых таких компонентов к коллекции схемы.  
  
 Неточная сериализация значений с плавающей запятой вызывает подобную проблему. Из-за алгоритма сериализации с плавающей запятой, используемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для подобных значений можно совместно использовать одну каноническую форму. Когда значение с плавающей запятой сериализовано и затем повторно вставлено, его значение может немного измениться. В редких случаях это может привести к значению, нарушающему любой из следующих аспектов для его типа при повторной вставке: **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**или **maxExclusive**. Чтобы это предотвратить, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отклоняет любые значения типов, полученных из `xs:float` или `xs:double` , которые не могут быть сериализованы и повторно вставлены.  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
