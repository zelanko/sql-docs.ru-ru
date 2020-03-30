---
title: Пользовательские свойства источника "XML" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52ce0e96ce131b1ea1a69f2ba9f7466850cbf4cf
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71290947"
---
# <a name="xml-source-custom-properties"></a>Пользовательские свойства источника «XML»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Источник «XML» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства источника «XML». Все свойства доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Целое число|Режим, используемый для доступа к XML-данным.|  
|UseInlineSchema|Логическое|Указывает, следует ли использовать в источнике «XML» определение встроенной схемы. Это свойство имеет значение по умолчанию **False**.|  
|XMLData|String|Файл или переменные, из которых следует получить XML-данные.<br /><br /> Значение этого свойства можно задать с помощью выражения свойства.|  
|XMLSchemaDefinition|String|Полный путь и имя файла определения схемы (XSD).<br /><br /> Значение этого свойства можно задать с помощью выражения свойства.|  
  
 В следующей таблице описаны пользовательские свойства выхода источника «XML». Все свойства доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|String|Определяет набор строк, связанный с выходом.|  
  
 Выходные столбцы источника «XML» не имеют пользовательских свойств.  
  
 Дополнительные сведения см. в статье [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
