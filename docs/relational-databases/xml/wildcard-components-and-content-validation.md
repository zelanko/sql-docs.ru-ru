---
title: Компоненты-шаблоны и проверка достоверности содержимого | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dbb4ecd59362c016536aed6731d5418cbe88d616
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674422"
---
# <a name="wildcard-components-and-content-validation"></a>Компоненты-шаблоны и проверка достоверности содержимого
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Компоненты-шаблоны используются для увеличения гибкости в том, в чем это разрешено для модели содержимого. Эти компоненты поддерживаются в языке XSD следующими способами.  
  
-   Компоненты-шаблоны элемента. Они представлены элементом **\<<xsd:any>**.  
  
-   Компоненты-шаблоны атрибута. Они представлены элементом **\<<xsd:anyAttribute>**.  
  
 Оба элемента-шаблона — **\<xsd:any>** и **\<xsd:anyAttribute>**  — поддерживают использование атрибута **processContents**. Это позволяет задать значение, указывающее, как приложения XML обрабатывают проверку правильности содержимого документа, связанную с этими элементами символа-шаблона. Они являются различными значениями, и их действие заключается в следующем.  
  
-   Значение **strict** указывает, что содержимое полностью подтверждено.  
  
-   Значение **skip** указывает, что содержимое не подтверждено.  
  
-   Значение **lax** указывает, что только элементы и атрибуты, для которых определения схемы являются доступными, будут подтверждены.  
  
## <a name="lax-validation-and-xsanytype-elements"></a>Нестрогая проверка и элементы xs:anyType  
 В спецификации XML-схемы для элементов типа **anyType** используется **нестрогая** проверка. Поскольку в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] нестрогая проверка не поддерживалась, к элементам **anyType**применялась строгая проверка. Начиная с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], предоставляется поддержка нестрогой проверки. Содержимое элементов типа **anyType** будет осуществляться при помощи нестрогой проверки.  
  
 Следующий пример демонстрирует использование нестрогой проверки. Элемент `e` схемы принадлежит типу **anyType** . В примере создаются типизированные переменные **xml** и демонстрируется нестрогая проверка элемента типа **anyType** .  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="https://www.w3.org/2001/XMLSchema"   
        targetNamespace="https://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 Выполнение следующего примера завершится без ошибок, поскольку успешно завершается проверка `<e>` :  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="https://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 Следующий пример завершается успешно. Экземпляр принимается, несмотря на то, что элементы `<c>` в схеме не определены.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="https://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 В следующем примере экземпляр XML отклонен, потому что определение элемента `<a>` не допускает строковых значений.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="https://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
