---
title: Введение в работу с Дельтами в SQLXML 4.0 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 567c4b6054623fad160dc17378e2a4a680fc4c8e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669513"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a>Введение в работу с дельтами в SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе приводится краткое введение в дельты (DiffGram).  
  
## <a name="diffgram-format"></a>Формат дельт  
 Общий формат дельты имеет вид:  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="https://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 Формат дельты состоит из следующих блоков.  
  
 **\<DataInstance >**  
 Имя этого элемента **DataInstance**, используется для в этом документе. Например, если дельты был сформирован из набора данных в .NET Framework, значение **имя** свойства набора данных будет использоваться как имя этого элемента. Этот блок содержит все соответствующие данные после изменения, в том числе, возможно, данные, которые не были изменены. Логика обработки дельты не учитываются элементы этого блока, для которого **diffgr: HasChanges** атрибут не указан.  
  
 **\<diffgr:before>**  
 Этот необязательный блок содержит исходные экземпляры (элементы) записи, которые необходимо обновить или удалить. Все базы данных таблицы, изменяемые (обновляемые или удаляемые) с помощью дельты должно отображаться в качестве элементов верхнего уровня в  **\<перед >** блока.  
  
 **\<diffgr: Errors >**  
 Этот необязательный блок не учитывается средствами обработки дельт.  
  
## <a name="diffgram-annotations"></a>Заметки дельт  
 Эти заметки определяются в пространстве имен DiffGram **«urn: schemas-microsoft-com: XML-diffgram-01»**:  
  
 **идентификатор**  
 Этот атрибут используется для сопоставления элементов в  **\<перед >** и  **\<DataInstance >** блоков.  
  
 **hasChanges**  
 Для операции обновления или вставки дельта должна задавать этот атрибут со значением **вставлены** или **изменения**. Если этот атрибут отсутствует, соответствующий элемент в  **\<DataInstance >** учитывается средствами обработки и обновления не выполняются. Рабочие образцы см. в разделе [примеры дельт &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
 **parentID**  
 Этот атрибут используется для определения связи «родители-потомки» между элементами в дельте. Этот атрибут присутствует только в \<перед > блока. Он используется в SQLXML при применении обновлений. Связь типа «родители-потомки» используется для определения порядка, в котором обрабатываются элементы дельты.  
  
## <a name="understanding-the-diffgram-processing-logic"></a>Основные сведения о средствах обработки дельт  
 В средствах обработки дельт используются определенные правила для определения того, является ли операция вставкой, обновлением или удалением. Описание этих правил приведено в следующей таблице.  
  
|Операция|Описание|  
|---------------|-----------------|  
|Insert|Дельта задает операцию вставки, если элемент присутствует в  **\<DataInstance >** блок, но отсутствует в соответствующем  **\<перед >** блока, а также **diffgr: HasChanges** указан атрибут (**diffgr: HasChanges = вставлены**) в элементе. В этом случае дельта применяется для вставки экземпляра записи, указанной в  **\<DataInstance >** блок в базу данных.<br /><br /> Если **diffgr: HasChanges** атрибут не указан, то элемент учитывается средствами обработки и вставка не выполняется. Рабочие образцы см. в разделе [примеры дельт &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).|  
|Update|Дельта задает операцию обновления, если элемент, в \<перед > блока, для которого отсутствует соответствующий элемент в  **\<DataInstance >** блоков (то есть оба элемента имеют **diffgr: ID** атрибут с тем же значением) и **diffgr: HasChanges** указан атрибут со значением **изменения** для элемента в  **\<DataInstance >** блока.<br /><br /> Если **diffgr: HasChanges** атрибут не указан для элемента в  **\<DataInstance >** блока, возвращается сообщение об ошибке с помощью логики обработки. Рабочие образцы см. в разделе [примеры дельт &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).<br /><br /> Если **diffgr: parentID** указывается в  **\<перед >** блокировать родительско дочернее отношение элементов, которые определяются **parentID** используются в Определение порядка, в котором записи обновляются.|  
|DELETE|Дельта задает операцию удаления, если элемент присутствует в  **\<перед >** блок, но отсутствует в соответствующем  **\<DataInstance >** блока. В этом случае дельта применяется для удаления экземпляра записи, указанной в  **\<перед >** блок из базы данных. Рабочие образцы см. в разделе [примеры дельт &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).<br /><br /> Если **diffgr: parentID** указывается в  **\<перед >** блокировать родительско дочернее отношение элементов, которые определяются **parentID** используются в Определение порядка, в котором записи будут удалены.|  
  
> [!NOTE]  
>  Передача параметров в дельты не предусмотрена.  
  
  
